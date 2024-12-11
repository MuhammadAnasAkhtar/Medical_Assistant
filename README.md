# Medical_Assistant Application


This project creates a medical chatbot using LangChain, Pinecone, and a local model for question-answering from a collection of documents. The chatbot is designed to answer medical-related questions by leveraging embeddings, document retrieval, and a conversational AI model.

## Project Overview

The chatbot is built using Flask, LangChain, Pinecone, and a custom Llama-2 model. The core components of the system include:

1. **Flask Web Application**: A simple web server to handle user inputs and return responses.
2. **Document Search**: Pinecone is used to store and retrieve document embeddings for fast and efficient search.
3. **Language Model**: CTransformers is used to load a Llama-2 model for conversational capabilities.
4. **Embedding**: Hugging Face embeddings are used to convert text into vector representations.
5. **Environmental Variables**: Uses `.env` file to load sensitive data such as API keys for Pinecone.

## Features

- **Question Answering**: Users can ask medical-related questions, and the chatbot will provide answers based on the documents indexed in Pinecone.
- **Document Retrieval**: The system searches for relevant information in the uploaded documents using embeddings and retrieves the most relevant chunks.
- **Flask Interface**: The chatbot is accessible via a web interface where users can chat with the bot.

## Setup Instructions

### Prerequisites

- Python 3.7 or higher
- Virtual Environment (recommended)
- Required libraries (listed below)

### Installation

1. **Clone the Repository**

   Clone this repository to your local machine:
   
   ```bash
   git clone https://github.com/your-username/medical-chatbot.git
   cd medical-chatbot
Create a Virtual Environment

It's recommended to create a virtual environment to manage dependencies:

bash
Copy code
python3 -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
Install Dependencies

Install the required Python libraries:

bash
Copy code
pip install -r requirements.txt
Set Up Environment Variables

Create a .env file in the root of the project and add the following keys:

bash
Copy code
PINECONE_API_KEY=your-pinecone-api-key
Replace your-pinecone-api-key with your actual Pinecone API key. You can obtain it from Pinecone's website.

Prepare Pinecone Index

Ensure you have already created a Pinecone index named medical. The chatbot will use this index for document retrieval.

Run the Flask Application

Once everything is set up, run the application:

bash
Copy code
python app.py
The application will start a Flask server on http://localhost:8080.

Access the Chatbot

Open a browser and go to http://localhost:8080 to interact with the chatbot.

# File Breakdown
app.py: Main Flask application that defines routes for the web interface and handles incoming requests.
src/helper.py: Contains helper functions like download_hugging_face_embeddings to fetch and prepare embeddings.
src/prompt.py: Defines the prompt template used by the language model.
templates/chat.html: Simple HTML template for the chatbot's web interface.
# Libraries Used
Flask: A micro web framework for Python.
LangChain: A framework for building language model-based applications.
Pinecone: A vector database used for storing and searching document embeddings.
CTransformers: A library for using transformer models like Llama.
Hugging Face: For embedding generation.
dotenv: Loads environment variables from a .env file.
# How It Works
Document Upload: The medical documents are loaded into Pinecone using the Hugging Face embeddings.
User Input: The user sends a question through the web interface.
Document Retrieval: The input query is passed to Pinecone, which retrieves relevant document chunks based on similarity.
Answer Generation: The retrieved documents are passed to the Llama-2 model, which generates a response using the context of the retrieved documents.
Response: The chatbot returns the response to the user.
# Future Enhancements
Real-time Document Upload: Allow users to upload new documents for indexing and retraining.
Improved UI: Enhance the user interface with additional features like chat history and multimedia support.
Scalability: Improve the system to support larger document collections and more complex queries.
# Acknowledgments
Pinecone: A vector database for fast and efficient document search.
LangChain: A powerful framework for building LLM-powered applications.
