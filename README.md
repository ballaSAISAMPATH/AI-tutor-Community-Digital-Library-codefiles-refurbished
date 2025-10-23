# 🤖 AI Textbook Tutor - Offline Local AI Project

Fully offline AI-powered Textbook Tutor supporting English and Telugu with Streamlit, LangChain, Ollama, ChromaDB, and HuggingFace embeddings.

=====================================================================

Overview
--------
This project provides two main Streamlit apps:

- Admin Panel: For uploading and managing PDF textbooks, generating embeddings, and building a local vector store.
- Tutor Interface: A multilingual AI chatbot interface for querying textbooks with voice input (Telugu), offline text-to-speech, and AI-powered answer generation using local LLM.

Features include:
- Offline embeddings and vector search with HuggingFace and ChromaDB.
- Local Ollama LLM (llama3.2) serving AI responses.
- Telugu speech recognition with faster-whisper and offline TTS with pyttsx3.
- Full offline mode fallback for privacy and resilience.

=====================================================================

Project Structure
-----------------
- admin_panel.py               Streamlit Admin Panel application
- admin_backend.py             Backend for admin PDF processing and management
- tutor_interface.py           Streamlit student-facing tutor app
- tutor_backend_multilingual.py  Multilingual tutor backend with ASR and TTS

=====================================================================

Installation & Setup
--------------------
1. Clone or download the project to your local machine.

2. Install Python 3.9+.

3. Create and activate Python virtual environment:

   python -m venv venv
   # Windows
   venv\Scripts\activate
   # macOS/Linux
   source venv/bin/activate

4. Create a requirements.txt file with:

   streamlit
   langchain-community
   langchain-text-splitters
   chromadb
   sentence-transformers
   langdetect
   requests
   faster-whisper
   torch
   pyttsx3
   pypdf

5. Install dependencies:

   pip install -r requirements.txt

6. Install Ollama (separately from Python):

   - Download and install from https://ollama.com/
   - Start Ollama server:

     ollama serve

   - Pull required model once:

     ollama pull llama3.2

7. Run Streamlit apps in separate terminals (with venv activated):

   streamlit run admin_panel.py
   streamlit run tutor_interface.py

8. Use Admin Panel to upload PDFs for building the offline database.
9. Use Tutor Interface to chat with your textbooks.

=====================================================================

Important Notes
---------------
- Keep ollama serve running for AI-powered features.
- Models and caches are stored locally under ./models and ./ai_tutor_db.
- Telugu voice input and TTS are fully offline.
- Full offline fallback available if Ollama is unavailable.

=====================================================================

Troubleshooting
---------------
- Missing packages? Run: pip install pypdf
- Ollama server not running? AI responses will be limited to basic textbook search.

=====================================================================

Made with ❤️ for offline AI learning
