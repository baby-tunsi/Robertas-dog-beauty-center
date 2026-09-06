# Roberta's Beauty Dog Center — Indice del progetto

Sito toilettatura con prenotazioni pubbliche e area staff. Stack: FastAPI + MongoDB (backend) e React 19 + Tailwind (frontend).

## Backend (`/app/backend/`)
| File | Descrizione |
|------|-------------|
| `server.py` | API FastAPI: auth (JWT cookie + codice `17052`), CRUD prenotazioni, availability, prenotazione manuale, seed staff |
| `requirements.txt` | Dipendenze Python |
| `.env` | `MONGO_URL`, `DB_NAME`, `JWT_SECRET`, `ADMIN_EMAIL`, `ADMIN_PASSWORD`, `STAFF_ACCESS_CODE`, `FRONTEND_URL` |

## Frontend (`/app/frontend/`)
### Configurazione
- `package.json`, `craco.config.js`, `tailwind.config.js`, `postcss.config.js`
- `.env` — `REACT_APP_BACKEND_URL`

### Sorgenti (`src/`)
| File | Ruolo |
|------|-------|
| `index.js` | Entry point React + QueryClient |
| `index.css` | Tema (cream/terracotta/sage), font Fraunces/Manrope, classi utility |
| `App.js` | Routing: `/`, `/staff/login`, `/staff/dashboard` |
| `App.css` | Wrapper minimale |
| `lib/api.js` | Axios instance con `withCredentials`, helper errori |
| `context/AuthContext.jsx` | Provider auth basato su cookie |
| `constants/testIds.js` | testids condivisi |
| `hooks/use-toast.js` | Hook toast Shadcn |
| `components/Header.jsx` | Nav con logo + menu mobile |
| `components/Hero.jsx` | Sezione hero con foto e CTA |
| `components/Services.jsx` | Griglia 5 servizi (bagno, taglio, unghie, orecchie, spa) |
| `components/About.jsx` | Chi siamo con statistiche |
| `components/BookingForm.jsx` | Modulo prenotazione pubblico (campi obbligatori, date + orari liberi) |
| `components/Contact.jsx` | Indirizzo, telefono, orari, mappa Google |
| `components/Footer.jsx` | Footer con link Area Staff |
| `components/ManualBookingDialog.jsx` | Dialog prenotazione manuale staff |
| `components/ui/*` | Shadcn UI components (button, card, dialog, calendar, ecc.) |
| `pages/HomePage.jsx` | Composizione della home |
| `pages/StaffLogin.jsx` | Accesso staff a 5 cifre (codice `17052`) |
| `pages/StaffDashboard.jsx` | Pannello staff: stats + prenotazione manuale + lista con verifica cliente e Conferma/Rifiuta |

### Static (`public/`)
- `index.html`, `manifest.json`, `robots.txt`, `favicon.ico`

## Memoria / documentazione
| File | Contenuto |
|------|-----------|
| `memory/PRD.md` | Requisiti, architettura, backlog |
| `memory/test_credentials.md` | Codice staff `17052` + endpoint |
| `auth_testing.md` | Playbook test auth |
| `design_guidelines.json` | Palette, tipografia, immagini |
| `INDEX.txt` | Elenco piatto di tutti i file inclusi nell'archivio |
| `INDEX.md` | Questo file |

## Endpoint principali (`/api`)
- `POST /auth/code-login` — body `{code:"17052"}`
- `POST /auth/logout`, `GET /auth/me`
- `GET /services`
- `GET /availability?date=YYYY-MM-DD`
- `POST /bookings` (pubblico, tutti i campi obbligatori)
- `POST /bookings/manual` (staff, blocca lo slot)
- `GET /bookings?status=…`, `GET /bookings/stats`
- `POST /bookings/{id}/confirm`, `POST /bookings/{id}/reject`, `DELETE /bookings/{id}`

## Archivio scaricabile
`/app/roberta-beauty-dog-center.zip` — sorgenti completi (esclusi `node_modules`, `.git`, `__pycache__`, `build`).
