# Medical Chatbot RAG System

A sophisticated medical question-answering system built using Retrieval Augmented Generation (RAG) techniques with advanced features such as reranking.

![Medical Chatbot Interface](docs/images/medical_chatbot_screenshot.png)
*Placeholder: Screenshot of the Medical Chatbot in action*

## 📋 Project Overview

This project implements a specialized medical chatbot that uses advanced RAG (Retrieval Augmented Generation) techniques to accurately answer medical questions. The system integrates medical documents (PDFs) into a knowledge base and retrieves relevant context to provide accurate, sourced responses to medical queries.

### Key Features

- **Document Ingestion**: Processes PDF medical documents and converts them into embeddings
- **Advanced RAG Techniques**: Uses various RAG approaches with increasing sophistication
- **Reranking**: Improves retrieval accuracy by reordering initial search results
- **Custom Prompting**: Specialized medical prompts for improved response generation
- **Gradio Interface**: User-friendly web UI for interacting with the system

## 🔧 Technologies Used

- **LLM**: Groq API (Llama3-8b-8192)
- **Embeddings**: BAAI/bge-small-en-v1.5
- **RAG Framework**: LlamaIndex
- **Reranking**: SentenceTransformer Reranking
- **UI**: Gradio

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Virtual environment (recommended)
- Groq API key (for LLM access)

### Installation

1. Clone this repository:
   ```
   git clone [your-repo-url]
   cd medical-chatbot-rag
   ```

2. Create and activate a virtual environment (optional but recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the project root and add your Groq API key:
   ```
   GROQ_KEY=your_groq_api_key_here
   ```

### Data Preparation

1. Place your medical PDF documents in the `data/` directory
2. The default setup works with files named med1.pdf, med2.pdf, etc.
3. For best results, ensure PDFs are well-structured and contain relevant medical information

### Running the Project

1. Launch the Jupyter notebook:
   ```
   jupyter notebook main.ipynb
   ```

2. Execute cells in sequence to:
   - Install dependencies
   - Process and embed documents
   - Create the vector index
   - Launch the Gradio interface

3. Access the Gradio interface via the URL displayed in the notebook output (typically http://127.0.0.1:7860)

## 📚 Using Your Own Data

To use this system with your own medical documents:

1. **Prepare Your Documents**:
   - Convert any document types to PDF format
   - Ensure readable text (not scanned images)
   - Place them in the `data/` directory

2. **Adjust Configuration** (if needed):
   - Modify the chunk size and overlap in the `text_chunker` configuration 
     - Smaller chunks (e.g., 128 tokens) for precise retrieval
     - Larger chunks (e.g., 512 tokens) for more context
   - Change the top-k parameters for retrieval and reranking based on your needs

3. **Select Appropriate Embeddings**:
   - The default model (BAAI/bge-small-en-v1.5) works well for general medical text
   - For specialized domains, consider using domain-specific embedding models

4. **Regenerate Vectors**:
   - Set `if True:` in the vector generation cell to create new embeddings for your data

## 🧠 Technical Concepts

### RAG (Retrieval Augmented Generation)

This project showcases multiple RAG implementations with increasing sophistication:

1. **Simple RAG**: Basic document retrieval and generation
2. **Enhanced RAG**: Custom prompt templates with top-k retrieval
3. **Reranking RAG**: Two-stage retrieval with reranking of initial results

### Reranking

Reranking improves retrieval quality by:
- First retrieving a larger set of potentially relevant documents (e.g., top-10)
- Then using a specialized reranker model to reorder results based on relevance
- Finally selecting only the most relevant documents (e.g., top-3) for generation

The project uses `SentenceTransformerRerank` with the `cross-encoder/ms-marco-MiniLM-L-2-v2` model, which significantly improves retrieval precision.

### Prompt Engineering

The system uses specialized medical prompts that:
- Instruct the model to behave as a medical expert
- Require it to answer solely based on retrieved context
- Prevent hallucination by requiring it to admit when context is insufficient

## 🤝 Contributing

Contributions to improve the Medical Chatbot RAG System are welcome:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- LlamaIndex for providing the RAG framework
- HuggingFace for hosting embedding and reranking models
- Groq for LLM API access
