# Chat with PDF Using RAG Pipeline Project

# 1. Overview
Imagine having a large PDF document and instantly getting answers to your questions without manually searching through pages. In this project, I’ve built an RAG pipeline that allows you to upload or fetch a PDF, ask a question about its content, and receive an accurate response. This system combines advanced Natural Language Processing techniques and tools like Hugging Face models, FAISS, and Sentence Transformers.


# 2. Architecture & Tools 

 1. PDF Retrieval: We use the requests library to download the PDF file from a provided URL.
 2. Text Extraction: PyMuPDF extracts textual data from the PDF. It supports multi-page PDFs and outputs clean text.
 3. Text Chunking: Since handling an entire document at once is inefficient, I split the text into smaller, manageable chunks of about 500 words each. This ensures both better embeddings and accurate query     matching.
 4. Embedding Generation: Using the SentenceTransformer model (all-MiniLM-L6-v2), I convert the text chunks into vector embeddings. These embeddings are numerical representations of text.
 5. Similarity Search with FAISS: The embeddings are stored in a FAISS index (a library for fast similarity search). When the user asks a question, the query is converted into an embedding, and the most relevant text chunks are retrieved based on similarity.
 6.Response Generation: Finally, the T5-small model from Hugging Face takes the retrieved text chunks and the user query as input, then generates a concise, relevant answer.

# Chat With Website Using Rag Pipline Project
# 1. Overview:
The project implements a Retrieval-Augmented Generation (RAG) pipeline that allows users to interact with structured and unstructured data scraped from websites. The system allows users to ask questions in natural language, and it will provide accurate, context-rich answers based on the information extracted from a set of predefined websites.

# 2. The pipeline follows a multi-step approach:

Crawl and Scrape Websites: Extract textual content (mainly from paragraphs) from a list of target websites.
Data Processing: Convert the extracted text into embeddings using a pre-trained model, store them in a vector database (FAISS), and associate them with metadata (such as the URL).
Query Handling: Accept a user query, convert it into a vector embedding, and search for the most relevant text chunks from the vector database.
Response Generation: Use a large language model (LLM) like BigScience BLOOM to generate a response, leveraging the retrieved chunks of data to ensure accuracy and context in the answer.
