# Shivendra Pratap Singh — Portfolio + Groq Chatbot

This is the premium responsive portfolio, refined with a fully wrapping hero headline with the oversized decorative watermark removed, restrained sage/charcoal palette, and floating **Ask Shivendra** profile chatbot.

## Portfolio
Open `index.html` through a local web server (for example, VS Code Live Server). Project screenshots are embedded directly in the HTML.

## Resume PDF
The `assets/Shivendra-Pratap-Singh-Resume.pdf` file powers the Resume section's embedded preview, View Resume link, and Download PDF button.

## Chatbot architecture
- Frontend: floating chat panel and “Ask AI” section embedded in `index.html`.
- Backend: `chatbot-backend/` (FastAPI + Groq). The Groq API key stays server-side.
- Profile source of truth: fixed resume and project details in `chatbot-backend/main.py`.
- Fallback responses work if the backend has no key or Groq is temporarily unavailable, but are limited.

## Run locally (Windows)

Terminal 1 — backend:

```powershell
cd chatbot-backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
```

Put your key in `chatbot-backend/.env`, then run:

```powershell
uvicorn main:app --reload --port 8000
```

Terminal 2 — portfolio:
- Open the portfolio folder in VS Code.
- Start Live Server for `index.html`.
- Click **Ask about Shivendra** in the bottom-right corner.

The frontend uses `http://127.0.0.1:8000` by default. The backend CORS setting allows common local development origins; add your exact origin to `ALLOWED_ORIGINS` if needed.

## Deploy

1. Deploy `chatbot-backend` as a separate Python service, such as Render.
2. Add `GROQ_API_KEY`, `GROQ_MODEL`, and `ALLOWED_ORIGINS` in the hosting provider's environment settings.
3. Set `ALLOWED_ORIGINS` to your exact deployed portfolio origin.
4. Replace `window.PORTFOLIO_CHAT_API` in `index.html` with the backend's public HTTPS URL.
5. Deploy the static portfolio to Vercel or another static host.

**Never put your Groq API key in the HTML/JavaScript or commit `.env`.**

## Accuracy note
The chatbot is constrained to facts from the supplied resume and known project information. It refuses unrelated topics and is instructed not to invent missing details. LLM output cannot be guaranteed hallucination-free; test representative recruiter questions before publishing.

## Contact
- Email: utyo135@gmail.com
- LinkedIn: https://www.linkedin.com/in/shivendra-pratap-singh-8bab22237
- GitHub: https://github.com/Shivendra1230
