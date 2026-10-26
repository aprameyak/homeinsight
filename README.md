# Home Inspection Summarizer

A small Express app that takes the issues from a home inspection and groups them by severity with an estimated repair total. It is for home buyers sorting through an inspection report.

## Features

- Submit a property with a list of issues, each with a type, severity, and cost
- Pulls out `urgent` and `major` issues into separate lists
- Adds up the estimated repair cost
- Saves results to a local `data.json` file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

The server runs on http://localhost:3016. Submit an inspection and list them:

```bash
curl -X POST http://localhost:3016/api/inspections \
  -H "Content-Type: application/json" \
  -d '{"property":"12 Oak St","issues":[{"type":"roof leak","severity":"urgent","cost":4000},{"type":"old water heater","severity":"major","cost":1200}]}'

curl http://localhost:3016/api/inspections
```

## How it works

- `server.js` is an Express server with `POST /api/inspections` and `GET /api/inspections`. POST returns the grouped analysis; GET returns the 50 most recent.
- Issues are entered as structured JSON. The app does not read inspection PDFs.
- Results are stored in `data.json` in the project folder, which is created on first run and ignored by git.
- `index.html` is served at the root URL but is still a generic placeholder form that is not connected to this API. `utils.js` contains helpers that `server.js` does not use yet.

## Status

Prototype. Manual data entry; the web page is not wired up, and there is no validation or authentication.

## License

MIT, see [LICENSE](LICENSE).
