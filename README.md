
# Project — AI PDF Assistant

## 1. Project Description

AI PDF Assistant is a Python web application that allows users
to upload text-based PDF documents and ask questions about their
contents using an OpenAI language model.

The application extracts selectable PDF text with pypdf,
provides a Streamlit chat interface, and sends the extracted
text and the user's question to the OpenAI API.

## 2. Project Objectives

- Upload and read PDF documents.
- Extract text while retaining page labels.
- Ask natural-language questions about a document.
- Generate answers grounded in supplied document text.
- Display a conversation interface in the browser.
- Handle common file and API errors.
- Keep API credentials outside the source code.

## 3. Technology Stack

- Python 3.10+
- Streamlit
- pypdf
- OpenAI Python SDK (OpenAI-compatible client)
- python-dotenv
- Groq API

## 4. Folder Structure

04_ai_pdf_assistant/
├── app.py
├── requirements.txt
├── .streamlit/
│   └── config.toml
├── .env
├── .env.example
├── .gitignore
└── README.md

Do not commit .env to version control.

## 5. Installation

Create and open the project directory, then create a virtual
environment.

Windows PowerShell:

    python -m venv .venv
    .venv\Scripts\Activate.ps1

macOS/Linux:

    python3 -m venv .venv
    source .venv/bin/activate

Install the dependencies:

    python -m pip install --upgrade pip
    pip install -r requirements.txt

## 6. API Configuration

Create a free Groq API key at https://console.groq.com/keys.

Copy .env.example to .env and set:

    GROQ_API_KEY=your-groq-api-key
    GROQ_MODEL=openai/gpt-oss-120b

The Groq free tier does not require a credit card, but rate
limits apply. You can change GROQ_MODEL to another available
Groq model if needed.

Never commit .env to GitHub.

## 7. Run the Application

Run the following command from the project directory:

    streamlit run app.py

Streamlit will provide a local address, usually:

    http://localhost:8501

Open that address in your browser.

## 8. How It Works

1. Streamlit receives the uploaded PDF.
2. The application validates the file size.
3. pypdf extracts selectable text from each page.
4. The extracted text is labeled with page numbers.
5. The text is limited to a configured character budget.
6. The user submits a question through the chat interface.
7. The application sends the document text and question
   to the configured Groq model.
8. The model generates a document-grounded answer.
9. Streamlit displays the answer.

## 9. Limitations

- Scanned PDFs require OCR, which is not included.
- Large documents are truncated.
- The application sends the entire retained text per question.
- The model can still produce inaccurate answers.
- Page references are requested but not independently verified.
- Previous conversation turns are displayed but not sent to
  the model, so follow-up context is limited.
- File size limits do not guarantee protection against every
  malformed or resource-intensive PDF.
- This is a prototype, not a production security system.

## 10. Privacy and Security

- Keep API credentials in environment configuration.
- Do not commit .env to version control.
- Avoid uploading sensitive documents unless authorized.
- PDF contents are sent to the configured AI API.
- Apply access controls, retention policies, logging controls,
  and additional file validation before deployment.

## 11. Future Improvements

- Implement retrieval-augmented generation (RAG).
- Split documents into chunks.
- Generate embeddings and retrieve relevant chunks.
- Add OCR for scanned PDFs.
- Add verified page-level citations and source snippets.
- Support context-aware conversation history.
- Add tests for PDF extraction, errors, and API failures.
- Add authentication and secure multi-user document storage.
- Deploy using a managed hosting service.

## 12. Example CV Description

Developed a Python-based AI PDF question-answering prototype
using Streamlit, pypdf, and the Groq API. Implemented PDF
text extraction, page labeling, configurable context limits,
chat-style interaction, and API error handling.

Use this description only after running, testing, and
understanding the project.