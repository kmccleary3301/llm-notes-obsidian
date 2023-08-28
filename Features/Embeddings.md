### Description
Embeddings are vector representations of text as well as context and corresponding labels. When used by an LLM, it can be queried in a way so that usage doesn't contribute to context, at least not as a direct sum of tokens as it is normally.


### Options

> [!faq]- Langchain
> Langchain is a framework for developing complex applications of language models. These can take the form of 'chains', which people can share. At the highest level, it allows LLMs to connect to other sources of data (Data-aware), and for LLMs to interact with their environments (Agentic).
> Their docs provide instructions on [referencing chat history](https://python.langchain.com/docs/use_cases/question_answering/how_to/chat_vector_db#return-source-documents), [citing sources](https://python.langchain.com/docs/use_cases/question_answering/how_to/qa_citations), [using local LLMs](https://python.langchain.com/docs/use_cases/question_answering/how_to/local_retrieval_qa), [web scraping](https://python.langchain.com/docs/use_cases/web_scraping/), [interacting with APIs](https://python.langchain.com/docs/use_cases/apis), [self-checking](https://python.langchain.com/docs/use_cases/more/self_check/), and many more.
>  

> [!faq]- txtai
> [Available Here](https://github.com/neuml/txtai)
> Txt ai is a massive embeddings database for LLM orchestration and workflows, pretty much a local package alternative to Langchain from what I can tell. 

### Examples
[Here](https://medium.com/@mayuresh.gawai/implementation-of-llama-v2-in-python-using-langchain-%EF%B8%8F-ebebe82e881b) is an example of using LangChain with quantized weights for LLaMA2 7b to query a document using [FAISS](https://github.com/facebookresearch/faiss) to answer questions. I've replicated the process in my own time and written custom instructions at [[LangChain Basic Document Query]].
