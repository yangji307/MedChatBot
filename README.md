# MedChatBot
## implementation method
### retriever
- chunking: using strategy "small to big", smaller chunks to larger chunks implemented by  LangChain
- embedding: ada-002 fine-tuning (https://docs.llamaindex.ai/en/stable/examples/finetuning/embeddings/finetune_embedding/)
- indexing: llama_index
- ranker: llama_index fine-tuning (https://docs.llamaindex.ai/en/stable/examples/finetuning/cross_encoder_finetuning/cross_encoder_finetuning/)
### generator
#### fine tuning
##### data generation method
- using llm generate question-answer pairs based on provided doc (https://docs.llamaindex.ai/en/stable/examples/finetuning/openai_fine_tuning/)
```angular2html
You are a vet Teacher/ Professor. Your task is to setup a quiz/examination. Using the provided context, formulate a single question that captures an important fact from the 
context. Restrict the question to the context information provided. each quesiton only includes one knowledege point. please provide no less than 100 q-a pairs.

You are a vet Teacher/ Professor. Your task is to setup a quiz/examination. Using the provided context, formulate 50 questions that captures important facts from the 
context. Try to distribute these questions throughout the various parts of the provided document. Restrict the question to the context information provided.
```
prompt for answering the question
```angular2html
You are an expert Q&A system that is trusted around the world. Always answer the query using the provided context information, and not prior knowledge.Some rules to follow:1. Never directly reference the given context in your answer.2. Avoid statements like 'Based on the context, ...' or 'The context information ...' or anything along those lines. now answer the following questions:
```

You are a vet Teacher/ Professor. Your task is to setup a quiz/examination. Using the provided context, formulate 50 complex questions that captures important facts from the 
context. Each question requires summarizing the information or at least two or three steps of reasoning to answer it. Try to distribute these questions throughout the various parts of the provided document. Restrict the question to the context information provided.

You are an expert Q&A system that is trusted around the world. Always answer the query using the provided context information, and not prior knowledge. Some rules to follow:1. Never directly reference the given context in your answer.2. Avoid statements like 'Based on the context, ...' or 'The context information ...' or anything along those lines. 3. Answer the queation directly in a smooth and natural manner, try to avoid beginning the answer with a heading or title. now answer the following questions: 