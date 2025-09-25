# InsightGrid Social Content Analytics

A lightweight Flask app that accepts PDFs and images, extracts text, and provides AI-driven engagement recommendations.

## Approach

I developed a lightweight Flask web application that allows users to upload PDFs and images to automatically extract text and generate actionable engagement insights. For PDFs, text extraction is handled using PyMuPDF, while images are processed with Tesseract OCR. The extracted content is then sent to an AI service, which provides recommendations for improving social media engagement, including optimizing post structure, captions, and hashtags.

The frontend features a clean, single-page HTML interface with drag-and-drop uploads, live previews for images and PDFs, and clear loading indicators, ensuring a smooth and responsive experience on both desktop and mobile devices. The backend provides a RESTful endpoint for requesting AI recommendations and includes error handling for unsupported file types or extraction issues, maintaining reliability and user confidence.

This solution emphasizes clarity, ease of deployment, and extensibility. Developers can easily swap the AI integration, add user authentication, or expand analytics. The application is lightweight, can run locally, or be deployed on cloud platforms, making it accessible to content creators, marketers, and small businesses seeking immediate, AI-driven feedback on their posts.

## Features

- Upload PDFs and images (drag-and-drop or file picker)
- Extract text from PDFs (PyMuPDF) and images (Tesseract OCR)
- AI recommendations via Gemini API (placeholder) or a local fallback
- Basic error handling and loading states

## Setup (Linux / macOS)

1. Install system dependencies:
   - Tesseract OCR (e.g., `sudo apt install tesseract-ocr` or on macOS `brew install tesseract`)
2. Create a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. (Optional) Set the Gemini API key and model in environment:
   ```bash
   export GEMINI_API_KEY="your_key_here"
   export GEMINI_MODEL="gemini-1.0"
   ```
4. Run the app:
   ```bash
   python app.py
   ```
5. Open http://127.0.0.1:5000 in your browser.

## 🚀 Live Demo

Check out the live project here: [Social Media Analyzer](https://insightgrid-social-content-analytics-1.onrender.com/)

## Outcome of the Project

### Loading Preview

![Loading](https://github.com/user-attachments/assets/780f1f26-29f3-4f65-bfa1-92624a96e36f)

### Generation Preview

![Data Generation](https://github.com/user-attachments/assets/c38ac5fb-7c8c-4762-8a70-e2edf889c8e2)

### Insights Preview

![Info](https://github.com/user-attachments/assets/81c84537-d8e7-46b7-97ba-7aec76dcf4dc)

## Notes

- The `call_gemini_for_recommendations` function uses a placeholder URL. Please replace with the official Gemini REST endpoint and adapt the request/response parsing per Google's docs.
- This project focuses on clarity and extensibility. You can add persistent storage, user accounts, or switch to a hosted AI provider easily.

## Deploying on Render (Native Python)

- Ensure `apt.txt` exists at the repo root with the line:
  ```
  tesseract-ocr
  ```
- Add a `Procfile` with:
  ```
  web: gunicorn app:app --workers 2 --threads 4 --timeout 120
  ```
- Build command: `pip install -r requirements.txt`
- Start command: `gunicorn app:app --workers 2 --threads 4 --timeout 120`
- Optional env var for custom path: `TESSERACT_CMD=/usr/bin/tesseract`
- On Windows, the app defaults to `C:\\Program Files\\Tesseract-OCR\\tesseract.exe` automatically.
