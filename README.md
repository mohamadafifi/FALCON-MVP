# Falcon MVP (Website + SMS)

## Quick Start
1) Install **Docker Desktop** (Mac/Windows) or Docker Engine (Linux).
2) Download this folder, copy `.env.example` to `.env`, fill in your keys.
3) From `infra/`, run:
   ```bash
   docker compose up -d --build
   ```
4) Open http://localhost:3000 for the web dashboard.
5) API health endpoint: http://localhost:8000/health

### Required Keys
- POLYGON_API_KEY (free at polygon.io) — for live quotes (otherwise workers use dummy values).
- TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN, TWILIO_FROM — for real SMS. Without these, alerts print to console.

### Where to put your watchlist CSV
Place your CSV anywhere and set `SYMBOLS` in `.env` (comma separated) for MVP.
Future step will load CSV into DB automatically.

### Troubleshooting
- If web can't fetch, ensure `NEXT_PUBLIC_API_URL` in `.env` is `http://localhost:8000`.
- If SMS doesn't arrive, check the alerts worker logs:
  ```bash
  docker compose logs alerts -f
  ```
