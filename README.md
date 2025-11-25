# AI Textbook Tutor - Offline Local AI for Learners

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

PART 1 :- Setup and Installation  - should only be done once

Terminal 1:
1. Create a virtual environment:  
   command:
   ```
   python -m venv venv
   ```

2. Activate the virtual environment:  
   - On Windows (PowerShell):  
     command:
     ```
     .\venv\Scripts\Activate.ps1
     ```
   - On Mac/Linux:  
     command:
     ```
     source venv/bin/activate
     ```

3. Install required packages:  
   command:
   ```
   pip install -r requirements.txt
   ```

4. Download necessary models:  
   command:
   ```
   python .\download_models.py
   ```

---

Terminal 2: Ollama Model Pull (One-time setup, no virtual environment)
- Download and install Ollama from https://ollama.com/
- Pull the model (llama3.2):
  command:
  ```
  ollama pull llama3.2
  ```
  Note: You only need to run this command once on your laptop. Subsequent uses of the model won't require pulling it again regardless of the folder.
- Close this terminal after pulling the model.

---

PART 2 :- Running the AI Tutor Prototype (Repeat Every Time You Start It)  
Note: remember to turn the internet off to experience the art of this prototype to answer any queries offline unlike online AI chatbots.  
Yeah, you don't need internet to get your queries solved, isn't that interesting .....

1. Terminal 1: Start Ollama server:
   command:
   ```
   ollama serve
   ```
   (If you encounter errors, see the debug section below.)

2. Terminal 2:  
   Activate virtual environment again:
   command:
   ```
   .\venv\Scripts\Activate.ps1
   ```
   Run the admin app:
   command:
   ```
   streamlit run .\admin_app.py
   ```

3. Terminal 3:
   Activate virtual environment:
   command:
   ```
   .\venv\Scripts\Activate.ps1
   ```
   Run the student multilingual app:
   command:
   ```
   streamlit run .\student_app_multilingual.py
   ```

So every time there will be 3 terminals running.

---

Error Debugs for Step 1 (If `ollama serve` Errors):

1. Check if Ollama is already running:
   command:
   ```
   tasklist | findstr ollama
   ```
2. For each process ID (PID) found, kill it by running:
   command:
   ```
   taskkill /PID <PID> /F
   ```
   Replace <PID> with the actual port/process ID from the previous command. Repeat if there are multiple.

Example output after 'tasklist | findstr ollama':
   ollama.exe                   1234 Console                    1     12,345 K
   command:
   ```
   taskkill /PID 1234 /F
   ```


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

Made by SAI SAMPATH BALLA for offline AI learning
