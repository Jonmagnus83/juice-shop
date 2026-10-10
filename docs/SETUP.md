# Lokal oppstart for læringslab

## Hva prosjektet er

OWASP Juice Shop er en **med vilje usikker** nettbutikk for juice. Den brukes til sikkerhetstrening, bevissthetsdemoer, CTF-er og til å prøve sikkerhetsverktøy. Appen inneholder sårbarheter fra [OWASP Top 10](https://owasp.org/www-project-top-ten) og andre feil som finnes i ekte webapplikasjoner.

Frontend er Angular (`frontend/`). Backend er Node.js og Express (`server.ts`, `routes/`), med SQLite via Sequelize (`models/`, `data/`).

Kjør den bare lokalt i en læringslab. Ikke bruk den som en ekte butikk, og ikke deploy filene under `infrastructure/` — de er en del av utfordringene og er med vilje usikre.

## Start lokalt

Du trenger [Node.js](https://nodejs.org) 22, 24 eller 26. Prosjektet bruker 24 som standardversjon.

```bash
npm install
npm start
```

`npm install` henter avhengigheter og bygger frontend og server via `postinstall`. `npm start` kjører den bygde appen (`node build/app`).

Åpne deretter <http://localhost:3000>.

Første oppstart kan ta litt tid fordi frontend bygges. Etter endringer i kildekoden kan du kjøre `npm install` på nytt. For utvikling med filovervåking finnes også `npm run serve`.

Andre installasjonsmåter (Docker, pakkede distribusjoner, Vagrant) står i [README](../README.md#setup).

## Mapper som betyr mest i læringslaben

| Mappe | Hvorfor den er nyttig |
| --- | --- |
| `frontend/src/` | Angular-klienten: sider, scoreboard og tjenester som snakker med API-et. |
| `routes/` | Express-endepunkter. Mye av butikklogikken ligger her. |
| `server.ts` | Setter opp serveren, middleware og hvilke ruter som monteres. |
| `models/` | Sequelize-modeller for brukere, produkter, handlekurv og utfordringer (SQLite). |
| `data/` | Oppretting av databasen. `data/static/challenges.yml` er katalogen over utfordringer. |
| `lib/` | Hjelpefunksjoner, oppstart (`lib/startup/`) og utfordringslogikk. |
| `views/` | Server-renderte maler (Handlebars og Pug). |
| `config/` | YAML-profiler, blant annet `default.yml`, `ctf.yml` og `tutorial.yml`. |
| `ftp/` | Filer som den simulerte FTP-katalogen deler ut. |
| `test/` | Tester: `test/server/`, `test/api/` og `test/cypress/`. |

Lengre introduksjon, arkitektur og løsningsguide: [offisiell prosjektside](https://owasp-juice.shop) og [Pwning OWASP Juice Shop](https://pwning.owasp-juice.shop).
