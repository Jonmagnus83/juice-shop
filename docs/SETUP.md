# Juice Shop for læringslab

## Hva prosjektet er

OWASP Juice Shop er en nettbutikk som er **med vilje usikker**. Den brukes til sikkerhetstrening, demoer og CTF-øvelser, og samler sårbarheter fra OWASP Top 10 og andre vanlige feil i ekte webapplikasjoner.

Appen består av et Angular-grensesnitt, en Express-server og en lokal SQLite-database. Den er et øvingsmiljø, ikke en mal for et ekte system.

## Start lokalt

Du trenger Node.js 22, 24 eller 26. Prosjektet bruker 24 som standard. Se kompatibilitetstabellen i [README.md](../README.md#nodejs-version-compatibility).

```bash
npm install
npm start
```

Åpne [http://localhost:3000](http://localhost:3000).

`npm install` henter avhengigheter og bygger frontend og server. Kjør det på nytt når avhengigheter eller bygg endres. `npm start` kjører den bygde serveren.

Noen utfordringer trenger en valgfri LLM eller `ALCHEMY_API_KEY`. Butikken starter uten dem. Serverloggen sier fra når en slik utfordring ikke kan løses.

Hvis `npm install` stopper med `Missing metafile: dist/frontend/stats.json`, er app-bundelen likevel bygd. Angular skriver `browser-stats.json`, mens SBOM-steget leser `stats.json`. Fullfør installasjonen slik:

```bash
cp frontend/dist/frontend/browser-stats.json frontend/dist/frontend/stats.json
npm --prefix frontend run sbom
npm run build:server
npm start
```

## Mapper som betyr mest i læringslaben

| Mappe | Hva du finner der |
| --- | --- |
| `server.ts`, `app.ts` | Oppstart av serveren |
| `routes/` | HTTP-endepunktene butikken svarer på |
| `frontend/src/` | Angular-grensesnittet, med sidene under `frontend/src/app/` |
| `models/` | Datamodeller mot SQLite |
| `data/static/` | Utfordringer (`challenges.yml`), brukere (`users.yml`) og kodefikser (`codefixes/`) |
| `lib/` | Felles logikk, blant annet `lib/startup/` og `lib/insecurity.ts` |
| `config/` | YAML-konfigurasjon, for eksempel `default.yml` og `ctf.yml` |
| `ftp/` | Filer som den simulerte FTP-katalogen deler ut |
| `views/` | Server-renderte maler |
| `test/` | Server-, API- og ende-til-ende-tester som viser forventet oppførsel |

`infrastructure/` og `infrastructure/terraform/` hører til kodeutfordringer. Ikke bruk dem til å rulle ut ekte infrastruktur.
