### Environment
```bash
conda create --name langchain_test python=3.9
conda activate langchain_test
pip install langchain[all] unstructured llama-cpp-python
```

### Document Sources
Using [llama-2-7b-chat.ggmlv3.q2_K.bin](https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGML/tree/main), as well as a document test.txt. Both in the same directory as the script.

### Script
```python
from langchain.llms import LlamaCpp
from langchain import PromptTemplate, LLMChain
from langchain.callbacks.manager import CallbackManager
from langchain.callbacks.streaming_stdout import (
    StreamingStdOutCallbackHandler
)
from langchain.vectorstores import FAISS
from langchain.embeddings import HuggingFaceInstructEmbeddings
from langchain.document_loaders import UnstructuredFileLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter

template = """Question: {question}

Answer:"""

prompt = PromptTemplate(template=template, input_variables=["question"])
callback_manager = CallbackManager([StreamingStdOutCallbackHandler()])

llm = LlamaCpp(
    model_path="llama-2-7b-chat.ggmlv3.q2_K.bin",
    n_ctx=6000,
    n_gpu_layers=512,
    n_batch=30,
    callback_manager=callback_manager,
    temperature = 0.9,
    max_tokens = 4095,
    n_parts=1,
)

llm_chain = LLMChain(prompt=prompt, llm=llm)


loader = UnstructuredFileLoader("test.txt")
documents = loader.load()
text_splitter = RecursiveCharacterTextSplitter(chunk_size=1000, chunk_overlap=50)
docs = text_splitter.split_documents(documents)

# embedding engine
hf_embedding = HuggingFaceInstructEmbeddings()

db = FAISS.from_documents(docs, hf_embedding)

# save embeddings in local directory
db.save_local("faiss_AiArticle")

# load from local
db = FAISS.load_local("faiss_AiArticle/", embeddings=hf_embedding)

while True:
    query = input("Enter question (Press enter to exit) -> ")
    if query == "":
        break
    print("Searching ")
    search = db.similarity_search(query, k=2)

    template = '''Context: {context}

    Based on Context provide me answer for following question
    Question: {question}

    Tell me the information about the fact. The answer should be from context only
    do not use general knowledge to answer the query'''

    prompt = PromptTemplate(input_variables=["context", "question"], template= template)
    final_prompt = prompt.format(question=query, context=search)

    llm_chain.run(final_prompt)
```