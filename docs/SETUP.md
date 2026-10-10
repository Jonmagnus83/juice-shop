# Juice Shop – lokal oppstart og læringslab

## Hva prosjektet er

OWASP Juice Shop er en moderne, sårbar nettapplikasjon (Node.js + Angular) designet for sikkerhetstrening, CTF og bevisstgjøring. Den inneholder sårbarheter fra OWASP Top Ten og mange andre reelle feil. Dette er en fork for lokal læringslab – ikke bruk i produksjon.

## Starte lokalt

Forutsetninger: Node.js 22–26 (se README.md for detaljer).

```bash
git clone https://github.com/Jonmagnus83/juice-shop.git
cd juice-shop
npm install          # installerer avhengigheter + bygger frontend
npm start            # starter server på http://localhost:3000
```

Åpne http://localhost:3000 i nettleseren.

Alternativt for utvikling (hot reload):
```bash
npm run serve:dev
```

## Viktigste mapper for læringslab

| Mappe | Hva den brukes til |
|-------|--------------------|
| `frontend/` | Angular-frontend (klientside-sårbarheter, XSS, DOM) |
| `routes/` | API-ruter og server-endepunkter (injection, auth, business logic) |
| `models/` | Datamodeller (Sequelize) |
| `data/` | Database-seed og statiske data |
| `lib/` | Delt forretningslogikk og hjelpefunksjoner |
| `server.ts` / `app.ts` | Hovedserver-oppstart |
| `views/` | Server-side visninger |
| `ftp/` | FTP-relaterte challenges |
| `config/` | Konfigurasjon |

Start med `routes/` og `frontend/` for de fleste utfordringer. Se offisiell companion guide for løsninger: https://pwning.owasp-juice.shop

**Merk:** Ikke endre sikkerhetsrelatert kode med mindre du bevisst jobber med en challenge. Dette er dokumentasjon only.
