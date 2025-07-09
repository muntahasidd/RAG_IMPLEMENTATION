Retrieval-Augmented Generation (RAG) using LangChain & Hugging Face

This project implements a simple RAG (Retrieval-Augmented Generation) system using publicly available models from Hugging Face, without relying on OpenAI. It scrapes website content, embeds it using MiniLM, stores it in a vector database, and generates context-based answers using a lightweight text generation model (flan-t5-base or flan-t5-large).


---

🔧 Features

✅ Web scraping using LangChain's WebBaseLoader

✅ Text splitting for long content

✅ Embedding with sentence-transformers/all-MiniLM-L6-v2

✅ Vector storage using Chroma

✅ Context retrieval using LangChain's retriever

✅ Question answering using flan-t5-base or flan-t5-large

✅ Fully local (no OpenAI key needed)



---

📦 Dependencies

Make sure you have the following installed (in Google Colab or local):

pip install langchain langchain-community langchain-huggingface chromadb transformers sentence-transformers


---

🔑 Authentication

Set your Hugging Face token:

import os
os.environ["HUGGINGFACEHUB_API_TOKEN"] = "your_token"
os.environ["HF_TOKEN"] = "your_token"


---

🚀 How It Works

1. Scrape the website
Loads content using:

from langchain_community.document_loaders import WebBaseLoader


2. Split the text
Using RecursiveCharacterTextSplitter to chunk large text.


3. Generate embeddings
Embeds text with:

from langchain_huggingface import HuggingFaceEmbeddings


4. Store in Chroma vector DB


5. Create retriever
Retrieves relevant chunks based on query.


6. Use a local LLM
Generates final answers using:

from transformers import pipeline
model="google/flan-t5-base"


7. Ask questions
You can now invoke:

rag_chain.invoke("Your question here")





**Notes**

Use flan-t5-base for faster performance on free Colab.

Avoid long context inputs — trim or truncate if needed.

Open-source models may not be as accurate as OpenAI’s GPT, but they're free and fast to experiment with.

