# SANDIKALE KASIR — PROJECT RULES

## 1. Scope
This project is a single-file HTML POS application for SANDIKALE. Existing features must be preserved unless a requested change explicitly removes them.

## 2. Seven-Layer Development Standard
Every change must be evaluated in this order: Monitoring, Deploy, Environment Variables, Database, Test, Rules File, Application/Index.

## 3. Current Architecture
- Runtime: browser
- Main application: `SANDIKALE_Kasir_7LAYER_2026-11-02.html`
- Persistence: browser `localStorage`
- Backup: embedded JSON inside the HTML
- No server database is currently active in this standalone build

## 4. Security
- Never place API keys, service-role keys, private tokens, or secrets in frontend source.
- Current user PINs are client-side application data and therefore are NOT secure production authentication. Do not describe this build as secure multi-user authentication.
- A future production authentication layer must move credentials to a backend/auth provider (e.g. Supabase Auth) and apply RLS/server-side authorization.

## 5. Database
`localStorage` is treated as a local persistence layer, not a multi-device database. Do not claim cross-device synchronization until a real backend database is implemented and tested.

## 6. Environment
The current standalone build has no required private environment variables. Public CDN/library URLs are configuration, not secrets. If Supabase or another backend is introduced, use environment variables and never hard-code secret keys.

## 7. Monitoring
The app includes `SandikaleMonitor` for boot/data diagnostics and runtime error logging. Important failures must be recorded and reported before declaring READY.

## 8. Testing
After important changes, test: boot, login, local persistence, product data, order flow, shift flow, history/report views, export/print paths, responsive layout, and regression of existing features.

## 9. Deployment
The current build can be served as a static HTML file. Static hosting does not solve authentication or multi-device synchronization. Those are separate architecture requirements.

## 10. Change Discipline
Do not modify unrelated files. Do not remove existing functionality without a stated reason. Prefer the smallest stable change.
