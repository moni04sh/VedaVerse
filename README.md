# VedaVerse is a Python-based Retrieval-Augmented Generation (RAG) multimedia assistant. It ingests audio, PDFs, images and screenshots, extracts and indexes textual content, and returns context-grounded responses by combining retrieval with a language model adapter. A Django-backed module provides persistence and simple web-serving capabilities.

## Key features
- Audio transcription (audio → text)
- PDF parsing & OCR extraction
- Image / screenshot handling
- Text chunking and retrieval (vector-search style RAG flow)
- LLM adapter for contextual generation
- Django backend for persistence, uploads and serving assistant interactions
- Helper scripts and optional browser automation for data acquisition

## Repository layout (high level)
- rag/
  - main.py — orchestration entrypoint
  - jarvis.py — CLI/agent wrapper
  - audio_to_text.py — audio ingestion / ASR utilities
  - sketch_screenshot.png, img.jpeg — example images
  - edu_rag/ed/ — Django project
    - manage.py, db.sqlite3, media/, static/
    - app/
      - assistant.py — RAG orchestration (retrieval + generation)
      - gemini.py — LLM adapter / provider abstraction
      - audio_text.py — audio transcription helpers
      - pdf.py — PDF parsing & text extraction
      - models.py — Django models for documents, indexes, conversations
      - frames.py, sketch.py — image/frame utilities
      - tests.py — unit tests
      - msedgedriver.exe — Selenium Edge driver (Windows binary included)

## Architecture overview
1. Ingest: audio, PDFs and images are processed to extract text (transcription + OCR).
2. Index: extracted text is chunked and prepared for retrieval (vector-based retrieval expected).
3. Retrieve + Generate: assistant fetches relevant chunks and uses the LLM adapter to produce grounded responses.
4. Persist & Serve: Django app stores documents, metadata and chat logs and can expose endpoints/UI.
5. Automate: Selenium utilities support automated ingestion and scraping workflows.

## System prerequisites (macOS)
- Python 3.10+
- Homebrew (recommended)
- Tools (as needed):
  - tesseract (OCR): brew install tesseract
  - ffmpeg (audio): brew install ffmpeg
  - browser driver for Selenium (chromedriver or geckodriver)

## Quickstart (development)
1. Clone repository and enter it:
   ```
   git clone <your-repo>
   cd Anon-main
   ```
2. Create and activate a virtual environment:
   ```
   python3 -m venv .venv
   source .venv/bin/activate
   ```
3. Install dependencies:
   - If a requirements.txt exists:
     ```
     pip install -r requirements.txt
     ```
   - Otherwise:
     ```
     pip install django requests pydub PyPDF2 pytesseract selenium python-multipart
     ```
4. Install system tools (macOS example):
   ```
   brew install tesseract ffmpeg
   brew install --cask chromedriver
   ```
5. Prepare and run the Django development server:
   ```
   cd rag/edu_rag/ed
   python manage.py migrate
   python manage.py runserver 127.0.0.1:8000
   ```
6. Run assistant entrypoints from the repository root:
   ```
   python rag/main.py
   # or
   python rag/jarvis.py
   ```

## Common tasks
- Ingest a PDF: use functions in rag/edu_rag/ed/app/pdf.py to parse and add a document to the index.
- Transcribe audio: use rag/audio_to_text.py or rag/edu_rag/ed/app/audio_text.py to convert audio files to text.
- Ask a question: run jarvis.py or call the assistant through the Django interface; the assistant will retrieve context and generate a response.

## Development & tests
- Run Django tests:
  ```
  cd rag/edu_rag/ed
  python manage.py test
  ```
- Add tests in rag/edu_rag/ed/app/tests.py for new features and bug fixes.

## Extending the project
- LLM adapter: customize or add provider-specific logic in rag/edu_rag/ed/app/gemini.py.
- Vector store: integrate FAISS, Chroma, Milvus or a managed vector DB and update index management code.
- Automation: replace msedgedriver.exe with a platform-appropriate driver and update Selenium configuration.

## Notes
- Review assistant and adapter modules to understand prompts, retrieval logic, and integration points before production use.
- Add a requirements.txt and any platform-specific setup details as needed for collaborators.
```// filepath: /Users/monish/Desktop/Anon-main/README.md
# Anon-main

Anon-main is a Python-based Retrieval-Augmented Generation (RAG) multimedia assistant. It ingests audio, PDFs, images and screenshots, extracts and indexes textual content, and returns context-grounded responses by combining retrieval with a language model adapter. A Django-backed module provides persistence and simple web-serving capabilities.

## Key features
- Audio transcription (audio → text)
- PDF parsing & OCR extraction
- Image / screenshot handling
- Text chunking and retrieval (vector-search style RAG flow)
- LLM adapter for contextual generation
- Django backend for persistence, uploads and serving assistant interactions
- Helper scripts and optional browser automation for data acquisition

## Repository layout (high level)
- rag/
  - main.py — orchestration entrypoint
  - jarvis.py — CLI/agent wrapper
  - audio_to_text.py — audio ingestion / ASR utilities
  - sketch_screenshot.png, img.jpeg — example images
  - edu_rag/ed/ — Django project
    - manage.py, db.sqlite3, media/, static/
    - app/
      - assistant.py — RAG orchestration (retrieval + generation)
      - gemini.py — LLM adapter / provider abstraction
      - audio_text.py — audio transcription helpers
      - pdf.py — PDF parsing & text extraction
      - models.py — Django models for documents, indexes, conversations
      - frames.py, sketch.py — image/frame utilities
      - tests.py — unit tests
      - msedgedriver.exe — Selenium Edge driver (Windows binary included)

## Architecture overview
1. Ingest: audio, PDFs and images are processed to extract text (transcription + OCR).
2. Index: extracted text is chunked and prepared for retrieval (vector-based retrieval expected).
3. Retrieve + Generate: assistant fetches relevant chunks and uses the LLM adapter to produce grounded responses.
4. Persist & Serve: Django app stores documents, metadata and chat logs and can expose endpoints/UI.
5. Automate: Selenium utilities support automated ingestion and scraping workflows.

## System prerequisites (macOS)
- Python 3.10+
- Homebrew (recommended)
- Tools (as needed):
  - tesseract (OCR): brew install tesseract
  - ffmpeg (audio): brew install ffmpeg
  - browser driver for Selenium (chromedriver or geckodriver)

## Quickstart (development)
1. Clone repository and enter it:
   ```
   git clone <your-repo>
   cd Anon-main
   ```
2. Create and activate a virtual environment:
   ```
   python3 -m venv .venv
   source .venv/bin/activate
   ```
3. Install dependencies:
   - If a requirements.txt exists:
     ```
     pip install -r requirements.txt
     ```
   - Otherwise:
     ```
     pip install django requests pydub PyPDF2 pytesseract selenium python-multipart
     ```
4. Install system tools (macOS example):
   ```
   brew install tesseract ffmpeg
   brew install --cask chromedriver
   ```
5. Prepare and run the Django development server:
   ```
   cd rag/edu_rag/ed
   python manage.py migrate
   python manage.py runserver 127.0.0.1:8000
   ```
6. Run assistant entrypoints from the repository root:
   ```
   python rag/main.py
   # or
   python rag/jarvis.py
   ```

## Common tasks
- Ingest a PDF: use functions in rag/edu_rag/ed/app/pdf.py to parse and add a document to the index.
- Transcribe audio: use rag/audio_to_text.py or rag/edu_rag/ed/app/audio_text.py to convert audio files to text.
- Ask a question: run jarvis.py or call the assistant through the Django interface; the assistant will retrieve context and generate a response.

## Development & tests
- Run Django tests:
  ```
  cd rag/edu_rag/ed
  python manage.py test
  ```
- Add tests in rag/edu_rag/ed/app/tests.py for new features and bug fixes.

## Extending the project
- LLM adapter: customize or add provider-specific logic in rag/edu_rag/ed/app/gemini.py.
- Vector store: integrate FAISS, Chroma, Milvus or a managed vector DB and update index management code.
- Automation: replace msedgedriver.exe with a platform-appropriate driver and update Selenium configuration.
