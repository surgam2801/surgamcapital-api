# Surgam Capital API

Backend API for Surgam Capital, built with Express, tRPC 11 and Drizzle ORM.

## Mutual fund features (`server/mf/`)

| Module | What it does |
| --- | --- |
| `amfi.ts` | Scheme master and latest NAV from AMFI's public daily NAV file (Regular Growth plans), refreshed every 6 hours, cached in `.data/` |
| `history.ts` | NAV history by AMFI code (public mirror at api.mfapi.in), returns, rate-limited with backoff |
| `auth.ts` | Phone + OTP sign-in, signed bearer token. Dev mode (no `SMS_PROVIDER`) returns the OTP in the response |
| `store.ts` | Investors, orders, SIPs, goals. JSON file in `.data/` until the MySQL store is wired |
| `router.ts` | tRPC routers: `mf.*`, `investor.*`, `orders.*`, `goals.*` |

Shared maths and copy live in `shared/mf/` (also copied into the web app).
`drizzle/` is a copy of the schema from `surgamcapital-db`; keep the two in sync.

Payments are simulated and NFO listings are placeholders until a payment gateway, exchange
(BSE StAR MF / NSE NMF) and NFO feed are connected.

## Getting started

```bash
pnpm install   # or npm install
cp .env.example .env
pnpm dev       # http://localhost:3000, health check at /api/health
pnpm test
```

### Environment

```env
PORT=3000
NODE_ENV=development
EXPO_WEB_PREVIEW_URL=http://localhost:8081   # allows the local web app through CORS
DATABASE_URL=mysql://user:password@localhost:3306/surgamcapital   # optional for now
INVESTOR_JWT_SECRET=change-me                 # dev generates one in .data/ if unset
SMS_PROVIDER=                                 # unset = dev OTP mode
```

## Build for production

```bash
pnpm build
pnpm start
```
