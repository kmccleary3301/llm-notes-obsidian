
### Features possible via LangChain
* Analyzing documents via a vector database
* Citing sources via document search and retrieval with [FAISS](https://github.com/facebookresearch/faiss)
* Long term chat memory.
* Retrieving the latest information from a vector database of news articles, papers, textbooks, etc.

### [[Stable Diffusion]]
### [[Document Collections]]

### Toolchains
I'm thinking the frontend, in addition to other feature such as document collections, will allow easy selection of premade toolchains offered by LangChain.

### Code Interpreter
LangChain claims support for [self checking](https://python.langchain.com/docs/use_cases/code_understanding), even in the context of code. We could use this to try to replicate OpenAI's [Code Interpreter](https://www.nytimes.com/2023/07/11/technology/what-to-know-chatgpt-code-interpreter.html) for code quality verification.