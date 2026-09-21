# 20 Domain Flask + Gemini 3.1 Flash-Lite Chatbots

This package contains **20 independent chatbot folders**, each with the requested structure:
`app.py`, `config.py`, `.env`, `requirements.txt`, `templates/index.html`, plus `README.md`.

## Important naming
The first chatbot is **Carrier Assistant** (career/job domain), following the requested title.

## Features
- Flask + Gemini API
- Gemini model defaults to `gemini-3.1-flash-lite`
- No login/register
- Temporary per-browser session chat history
- Server-side Flask signed session cookie; no global shared conversation
- Strict domain prompt/guard so unrelated questions are declined
- `config.py` controls title, domain, prompt, behavior, welcome message, theme/accent, and PORT
- Responsive UI for mobile/tablet/laptop/desktop
- Different accent/theme settings across the 20 chatbots
- Render/Gunicorn compatible
- `PORT` can be supplied by Render

## Local setup
1. Open one chatbot folder.
2. Create/replace `.env`:
   `GEMINI_API_KEY=your_key_here`
   `FLASK_SECRET_KEY=replace_with_a_long_random_secret`
3. Install:
   `pip install -r requirements.txt`
4. Run:
   `python app.py`
5. Open the local address shown by Flask.

## Render deployment
For each chatbot, create a separate Render Web Service from its folder/repository.

Build Command:
`pip install -r requirements.txt`

Start Command:
`gunicorn app:app`

If the repository contains multiple chatbot folders, set Render **Root Directory** to the exact chatbot folder name. If the chatbot files are at repository root, leave Root Directory blank.

Add these Environment Variables in Render:
- `GEMINI_API_KEY` = your Gemini API key
- `FLASK_SECRET_KEY` = a long random secret
- optional `GEMINI_MODEL` = `gemini-3.1-flash-lite`

Do not commit a real API key to GitHub.

## Session privacy note
The application stores only the current conversation in the Flask session and limits history to the latest 20 messages. Sessions are isolated by the user's browser cookie. For stronger production privacy controls, use HTTPS, a strong secret, secure cookies, and an appropriate server-side session store.

## Changing a chatbot
Edit `config.py`:
- `CHATBOT_TITLE`
- `DOMAIN`
- `SYSTEM_PROMPT`
- `BEHAVIOR`
- `WELCOME_MESSAGE`
- `UI_THEME`
- `UI_ACCENT`
- `PORT`

The domain prompt is injected on every Gemini request. It instructs the model to refuse unrelated questions.

## Included domains
1. Career & Jobs
2. Travel & Tourism
3. Education & Learning
4. Programming & Software Development
5. Personal Finance Education
6. Fitness & Exercise
7. Cooking & Food
8. Home Improvement
9. Consumer Technology
10. Business & Entrepreneurship
11. Digital Marketing
12. General Legal Information
13. Languages & Communication
14. Books & Literature
15. General Science
16. History & Culture
17. Photography
18. Graphic & UI Design
19. Real Estate Education
20. Project Management

## This chatbot
**Design Assistant** — Graphic & UI Design
