# keelrail

**The non-custodial payment rail for AI & agent work.** Point any agent or app at
one endpoint; pay per call or per outcome in **USDC across chains** — or by
invoice. Providers plug in and settle through the rail; funds move peer-to-peer,
the rail never custodies them.

> Open interface, sovereign engine. Value in AI accrues at the **application
> layer**, not the model — so keelrail is the app + payment layer you own, running
> on open-weight models, on hardware you control.

---

## Why it exists
Open-source AI's missing piece is **monetization + payments for the people who run
it.** keelrail is that layer:

- **Metered access** — pay only for what you use (token-metered or flat per call).
- **Per-outcome agent work** — layered execution (plan → verify → refine), not one-shot.
- **Private behavior products** — buy *how* a model thinks, without exposing internals.
- **Rail-as-a-service** — other providers plug in, get paid, keep their keys; the
  rail takes a platform fee, non-custodially.
- **Sovereign** — runs on owned hardware; data never leaves your control.

## Quickstart (client)
```bash
# discover what's available + how to pay
curl https://<host>/x402.json

# call a paid endpoint (out of balance -> HTTP 402 with pay-to instructions)
curl https://<host>/v1/agent/run \
  -H "authorization: Bearer <key>" \
  -d '{"task":"...","model":"..."}'
```

## Endpoints
| Path | Capability | Price (default) |
|---|---|---|
| `POST /v1/chat/completions` | metered inference | $0.50 / 1k tokens |
| `POST /v1/agent/run` | layered agent task | $2 / run |
| `POST /v1/audit` | defensive security audit (authorized targets) | $5 |
| `POST /v1/data/generate` | synthetic datasets | $0.05 / sample |
| `POST /v1/fix` | config repair (nginx/YAML/Dockerfile/.env) | $0.05 |
| `POST /v1/tz/meeting` | timezone / meeting math | $0.02 |
| `GET  /x402.json` | agent-discovery manifest | free |

## Payment (x402 / USDC)
When your balance is empty the rail returns **HTTP 402** with a pay-to address and
supported networks (Base, Arbitrum, Polygon, Optimism). Pay in USDC; your balance
credits after on-chain verification. Non-custodial throughout.

## Open interface, private engine
This repo is the **open interface** — discovery, client shape, docs. The engine
(models, prompts, methods, on owned hardware) is the sovereign product and is not
in this repo. That's open-core: the interface is free and forkable; the sovereign
engine is the paid layer.

## Support the project
If keelrail is useful, sponsorship keeps it moving — see `.github/FUNDING.yml`.

## License
MIT (this interface). "keelrail" and the engine are © Client Engine LC.
