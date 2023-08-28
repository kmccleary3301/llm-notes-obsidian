### Basic Idea
We will provide access to a finetuned instance of LLaMA2 70b with 16k context. Considering the state of LLaMA finetuning has surpassed ChatGPT on pretty much all metrics, the backend will utlilize LangChain for unique applications and feature support (see [[Features]]. The frontend will be written in React (possible Native) and will be designed to be user friendly with the more advanced features available in a settings panel. We want the immediately visible application to be minimal and user friendly, but with advanced features being no more than one to two clicks away.

### Access
My hope is that the application will be freely available to LSU students, and possibly available to businesses. The backend will utilize an API with oauth2 and access tokens, with tracking on usage. LSU students will have a daily token limit, but this should be high enough that only people abusing the service will hit it. 
Hopefully in the end the frontend will be available at a memorable LSU subdomain, like ai.lsu.edu.

### Backend
So far, it seems the backend will need to be written in python in order to support LangChain, but from my minimal reading we may need to use [exllama](https://github.com/turboderp/exllama) in order to extend the context of the model to 16k. I found [one thread](https://www.reddit.com/r/LocalLLaMA/comments/14fqfdu/how_to_use_langchain_with_exllama/) on integrating the two, but nothing else so far. 

### [[Training]]