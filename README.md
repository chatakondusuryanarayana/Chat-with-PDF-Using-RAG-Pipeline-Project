# Chat-with-PDF-Using-RAG-Pipeline-Project

# OVERVIEW
Imagine having a large PDF document and being able to instantly get answers to your questions without manually searching through pages. In this project, I’ve built a RAG pipeline that allows you to upload or fetch a PDF, ask a question about its content, and receive an accurate response. This system combines advanced Natural Language Processing techniques and tools like Hugging Face models, FAISS, and Sentence Transformers.


# 2. Architecture & Tools 

PDF Retrieval:

We use the requests library to download the PDF file from a provided URL.
Text Extraction:

The tool PyMuPDF extracts textual data from the PDF. It supports multi-page PDFs and outputs clean text.
Text Chunking:

Since handling an entire document at once is inefficient, I split the text into smaller, manageable chunks of about 500 words each. This ensures both better embeddings and accurate query matching.
Embedding Generation:

Using the SentenceTransformer model (all-MiniLM-L6-v2), I convert the text chunks into vector embeddings. These embeddings are numerical representations of text.
Similarity Search with FAISS:

The embeddings are stored in a FAISS index (a library for fast similarity search). When the user asks a question, the query is converted into an embedding, and the most relevant text chunks are retrieved based on similarity.
Response Generation:

Finally, the T5-small model from Hugging Face takes the retrieved text chunks and the user query as input, then generates a concise, relevant answer.
