# Express user API

A small Express API serving user and health endpoints, backed by an in-memory store. Used as the practice project for the Claude Code course.

## Commands
- `npm run dev` — start the API with auto-reload on http://localhost:3000
- `npm test` — run the test suite (Node's built-in test runner)
- `npm run lint` — check code style with ESLint

## Conventions
- Use CommonJS (`require` / `module.exports`), not ES module `import`.
- One route file per resource in `routes/`, mounted in `server.js`.
- All data access goes through `db/store.js` — don't read or mutate the users array directly from a route.
- Validate input in the route: return `400` for bad input and `404` for a missing record.

## Architecture
- `server.js` is the entry point: it creates the app, adds `express.json()`, mounts the route files, and only listens when run directly (so tests can import the app).
- `routes/` holds one router per resource (`users.js`, `health.js`).
- `db/store.js` is a tiny in-memory helper standing in for a database.
- `tests/` runs `node --test` with `supertest` against the exported app.
