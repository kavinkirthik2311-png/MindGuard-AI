# Build and verification notes

Changes made in this emergency package:
- Replaced hard-coded `/mindguard` BrowserRouter with HashRouter so GitHub Pages routes work under the repository's own URL path.
- Changed Vite asset base to relative (`./`) so the frontend is not tied to one GitHub account/repository name.
- Removed the stale `homepage` field pointing to another GitHub account.
- Added a deployment README explaining the frontend/backend separation and the need to set `VITE_API_URL` to the actual deployed backend.
- Added a wellness-report disclaimer: check-in scores are not a medical diagnosis.

Checks:
- Backend Python source compiles successfully.
- Existing backend unittest suite currently has 4 failures out of 8 tests before any live deployment test; these are pre-existing logic/test mismatches in the supplied project and are not claimed fixed.
- Frontend production build could not be verified in this environment because the Vite executable/dependencies were not available after dependency installation timed out.
- No live Render/GitHub Pages deployment or live LLM provider call was performed.

Important:
- The supplied `.env.production` still points to `https://mindguard-demo-ln8z.onrender.com/api`. Change it to the real backend URL you intend to use before publishing.
- The chat's interview logic currently contains heuristic scoring/defaults. Treat its scores as a demo estimate, not validated health data.
