Training day 14 report  
PDF-Based Question Answering System UsingRAG 
1. Introduction 
This project implements a Retrieval-Augmented Generation 
(RAG) system that allows users to ask questions from a 
PDF document. The system extracts text from a PDF file, 
divides it into meaningful chunks, stores them in a vector 
database, and later uses a generative AI model to answer 
user queries based on the retrieved content. 
The project combines document processing, vector storage, 
and generative AI to create an intelligent document-based 
question-answering system. 
2. Objective of the Project 
The main objectives of this project are: 
• To extract text from PDF documents 
• To split large text into manageable chunks 
• To store document chunks in a vector database 
• To retrieve relevant information efficiently 
• To generate accurate answers using Gemini AI 
3. Technologies and Libraries Used 
Programming Language 
• Python 
Libraries Used 
• PyMuPDF (fitz) – Extracts text from PDF files 
• ChromaDB – Stores and indexes text chunks 
• Google Generative AI (Gemini) – Generates 
intelligent answers 
• tiktoken – Tokenizes text for chunking 
• tqdm – Displays progress bar during indexing 
• OS Module – File and environment variable handling 
4. System Architecture 
The system follows a pipeline-based architecture: 
1. PDF document input 
2. Text extraction from PDF 
3. Token-based text chunking 
4. Indexing chunks into ChromaDB 
5. User question input 
6. Context-aware answer generation using Gemini 
7. Working of the System 
Step 1: API Setup 
The Gemini API key is configured using environment 
variables. The Gemini Pro model is initialized for text 
generation. 
Step 2: PDF Text Extraction 
The system reads the PDF file using PyMuPDF and 
extracts text from all pages. 
Step 3: Text Chunking 
The extracted text is converted into tokens using tiktoken. 
Overlapping chunks are created to preserve context 
between consecutive sections. 
Step 4: Indexing into ChromaDB 
Each text chunk is stored in ChromaDB along with 
metadata such as chunk index. 
Step 5: Question Input 
The user enters a question related to the PDF document. 
Step 6: Answer Generation 
Relevant chunks are retrieved and passed to the Gemini 
model, which generates a context-aware response. 
7. Features of the Project 
• Works with large PDF documents 
• Efficient text chunking using tokens 
• Persistent vector storage 
• Fast document indexing 
• AI-powered intelligent answers 
8. Advantages 
• Reduces hallucination using document grounding 
• Scalable to multiple PDFs 
• Faster search and retrieval 
• Accurate question answering 
• Suitable for reports, notes, and manuals 
9. Applications 
• Academic PDF analysis 
• Training document assistance 
• Research paper question answering 
• Corporate report analysis 
• Personalized learning systems 
10. Limitations 
• Requires internet connectivity 
• API key dependency 
• Large PDFs increase indexing time 
• Basic retrieval logic without ranking optimization 
11. Future Enhancements 
• Add semantic search ranking 
• Support multiple PDFs 
• Build a web interface 
• Add voice-based queries 
• Implement citation-based answers 
12. Conclusion 
The PDF-based RAG system successfully demonstrates 
how document retrieval and generative AI can work 
together 
to 
create 
intelligent 
question-answering 
applications. By combining ChromaDB for storage and 
Gemini for generation, the system ensures accurate and 
context-aware responses from PDF documents.
