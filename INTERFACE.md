# keelrail — public interface

Base URL: `https://<your-host>`  ·  Auth: `Authorization: Bearer <key>`

| Path | What | Billing |
|---|---|---|
| `POST /v1/chat/completions` | metered model inference | per token |
| `POST /v1/tz/*` | timezone / meeting math | flat per call |
| `POST /v1/data/generate` | synthetic datasets | per sample |
| `POST /p/{provider}/*` | rail-as-a-service (3rd-party) | provider price, platform fee split |
| `GET  /now` `/healthz` `/api/stats` | status | free |

Out of balance → **HTTP 402** with USDC pay-to across supported chains. Pay, then
your balance credits (on-chain verified). Internals (models, prompts, methods)
are never exposed.
