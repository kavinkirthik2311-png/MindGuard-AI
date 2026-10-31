# MindGuard AI — Exhibition build

This repository contains a React/Vite frontend and a Flask API backend.

## Frontend (GitHub Pages)

The frontend is configured to use relative asset paths and `HashRouter`, so it can run under a GitHub Pages repository URL without hard-coding `/mindguard`.

GitHub Actions builds `mindguard-frontend` and publishes `dist` when code is pushed to `main`.

The production API URL is configured in `mindguard-frontend/.env.production` as `VITE_API_URL`. Before publishing, make sure this points to the backend URL you actually deployed, ending in `/api`. A frontend-only deployment does not deploy the Flask backend.

## Backend (Render or another Python host)

- Root directory: `mindguard-backend`
- Build/install command: `pip install -r requirements.txt`
- Start command: `python app.py` (or `waitress-serve --listen=0.0.0.0:$PORT app:app` if the host expects a production WSGI server)
- The backend root `/` responds with a JSON health status.
- Configure `SECRET_KEY` securely on the host. Do not commit API keys or secrets.

## Important accuracy note

The wellness summary is a self-reflection aid, not a medical diagnosis. A score is only as reliable as the answers collected and the scoring rules; do not present it as a clinically validated assessment. Do not claim that an external AI provider is connected unless a live provider request has been tested successfully.

## Local development

Frontend:
```sh
cd mindguard-frontend
npm install
npm run dev
```

Backend:
```sh
cd mindguard-backend
pip install -r requirements.txt
python app.py
```

The Vite development server proxies `/api` to `http://localhost:5000`.
