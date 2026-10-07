# Resume-Analyzer
# 📄 ATS Resume Checker

Upload a resume (PDF or DOCX), optionally paste a job description, and get:

- An overall **ATS score** (0-100) and a breakdown by category
- Strengths and **missing keywords**
- Formatting issues that can break ATS parsing
- Prioritized, specific **improvements** with example rewrites

Built with [Streamlit](https://streamlit.io) and Google's Gemini Flash model.

## Run locally

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Get a free API key from https://aistudio.google.com/apikey, then either:

- paste it into the sidebar when the app runs, **or**
- create `.streamlit/secrets.toml` (never commit this file):

```toml
GEMINI_API_KEY = "your-key-here"
```

Start the app:

```bash
streamlit run app.py
```

## Deploy on Streamlit Community Cloud

1. Push this repo to GitHub.
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, pick the repo, branch `main`, main file `app.py`.
4. Under **Advanced settings → Secrets**, add: `GEMINI_API_KEY = "your-key-here"`
5. Click **Deploy**.

## Notes

- Scanned/image-only PDFs can't be read (ATS systems can't read them either).
- Resume text is sent to the Gemini API for analysis.
- The model name can be changed in the sidebar (default: `gemini-2.5-flash`).
- The score is an AI estimate, not the output of a real employer ATS.
