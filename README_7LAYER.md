# SANDIKALE Kasir — 7-Layer Development Baseline

## Current status
This baseline applies the 7-layer development workflow to the standalone SANDIKALE Kasir HTML build.

### Data source
The latest backup JSON is embedded into the HTML. On boot, the embedded backup initializes the local data store.

### Current persistence limitation
Data is stored in browser localStorage. Different devices/browsers do not automatically share the same transactions.

### Security limitation
The standalone build contains client-side user records/PINs. This is suitable for a local prototype/workstation workflow, but not equivalent to secure server-side authentication.

## 7-layer implementation
1. **Monitoring** — runtime error capture + boot/data diagnostics via `SandikaleMonitor`.
2. **Deploy** — static HTML is deployable to static hosting.
3. **Environment Variables** — no private secret is required by the current standalone build; future backend secrets must use environment variables.
4. **Database** — localStorage currently; backend migration remains a required future step for multi-device operation.
5. **Test** — static integrity and headless boot checks are required after changes.
6. **Rules File** — `CLAUDE.md` documents architecture, security, testing, and change rules.
7. **Application / Index** — existing POS application remains the main implementation.

## Production roadmap
RULES → DATABASE/AUTH → ENVIRONMENT → APPLICATION → TEST → DEPLOY → MONITORING

Do not mark the system production-ready for multi-device use until backend synchronization and secure authentication are implemented and tested.
