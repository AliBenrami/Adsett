# **Built at HackUTA 2025**

# Adsett — AI-Powered Ad Creative Feedback  
Smarter Ads. Sharper Insights.

Adsett is an AI-driven platform that helps creators and marketing teams analyze ad creatives, manage assets, and receive intelligent feedback.

---

# ⚡ Run Guide ⚡

## 1. Required Terminals
Run two terminals:

- Python Backend (FastAPI)
- Frontend (Next.js)

---

# 2. Prerequisites

Install:
- Python 3.10+
- Node.js 18+
- Auth0 account

Backend `.env` file (place inside `hackuta-backend/.env`):

    AUTH0_DOMAIN=
    AUTH0_CLIENT_ID=
    AUTH0_CLIENT_SECRET=
    SESSION_SECRET=
    FRONTEND_URL=http://localhost:3000
    S3_BUCKET_NAME=
    GOOGLE_API_KEY=
    GEMINI_API_KEY=
    DATABASE_URL=sqlite+aiosqlite:///./hackuta.db
    ENVIRONMENT=development

Frontend `.env.local` file (place inside `hackuta-frontend/.env.local`):

    NEXT_PUBLIC_API_URL=http://localhost:8000

---

# 3. Terminal 1 — Backend (FastAPI)

Run these commands:

    cd hackuta-backend
    python -m venv venv
    venv\Scripts\activate   (Windows)
    source venv/bin/activate   (macOS/Linux)
    pip install -r requirements.txt
    uvicorn app:app --reload --port 8000

---

# 4. Terminal 2 — Frontend (Next.js)

Run these commands:

    cd hackuta-frontend
    npm install
    npm run dev

The app will be available at:

    http://localhost:3000

---

# 5. Summary

Backend → http://localhost:8000  
Frontend → http://localhost:3000  
Login → Auth0  
You're ready to use the platform.

---

# 📡 API Highlights

- GET /auth/login  
- GET /auth/me  
- POST /images  
- POST /analyze/image  
- GET /images  

API Docs:  
http://localhost:8000/docs

---

# 🔐 Authentication Flow (Auth0)

1. User clicks login  
2. Frontend sends request to backend  
3. Backend redirects to Auth0  
4. Auth0 returns authorization code  
5. Backend exchanges code for profile  
6. Backend issues session token  
7. Frontend stores token  
8. User becomes authenticated  

All authentication logic is backend-controlled.

---

# 🧱 Tech Stack

Backend:
- FastAPI
- SQLAlchemy (async)
- Authlib (OAuth2)
- SQLite
- Python 3.10+

Frontend:
- Next.js 15
- React 19
- TypeScript
- Tailwind CSS

Authentication:
- Auth0 OAuth2
- Session tokens + httpOnly cookies

---

# 📂 Project Structure

    Adsett/
    ├── hackuta-backend/
    │   ├── app.py
    │   ├── oauth.py
    │   ├── session.py
    │   ├── database.py
    │   ├── models.py
    │   └── requirements.txt
    │
    ├── hackuta-frontend/
    │   ├── src/app/
    │   ├── src/components/
    │   ├── src/lib/
    │   └── package.json
    │
    └── SETUP_GUIDE.md

---

# 🛠 Development Notes

Backend:

    uvicorn app:app --reload

Frontend:

    npm run dev

Reset database:

    cd hackuta-backend
    rm hackuta.db
    python - <<EOF
    from database import init_db
    import asyncio
    asyncio.run(init_db())
    EOF

---

# 🐛 Troubleshooting

Login issues?
- Check Auth0 callback URL
- Verify backend .env
- Inspect backend logs
- Check browser console

Session issues?
- Check localStorage for session token
- Clear cookies + localStorage
- Try incognito mode

---

# 📄 License
MIT License — free to use and modify.
