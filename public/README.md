# From the Other Side

From the Other Side is a Scrimba project for sharing paranormal sightings. Read saved encounters, submit your own, or follow a live feed of ghost stories.

## Run locally

Use Node.js 22.16 or newer with npm. The server uses [`import.meta.dirname`](https://nodejs.org/api/esm.html#importmetadirname).

From the project root, run the following commands.

```sh
npm ci
npm start
```

Open [http://localhost:8000](http://localhost:8000). For development, use `npm run dev` to restart the server automatically when files change.

## Explore the app

- **Read** saved sightings and select **Read in full** to expand a story. [Sightings](http://localhost:8000/sightings.html)
- **Upload** a sighting with a title, details, date and time, and location. Submitted sightings appear on the Read page. [Upload a sighting](http://localhost:8000/upload-sighting.html)
- **Live News** shows a random story from the built-in collection every three seconds via Server-Sent Events. [Live News](http://localhost:8000/news.html)

## How it works

The frontend uses HTML, CSS, and browser JavaScript. The Node.js server uses the built-in `node:http` module to serve the pages and handle API requests. Sightings are stored in [data/data.json](../data/data.json), and the live feed draws from [data/stories.js](../data/stories.js).

| Endpoint | What it does |
| --- | --- |
| `GET /api` | Returns the saved sightings as JSON. |
| `POST /api` | Accepts a JSON sighting with `title`, `text`, `timeStamp`, and `location`. The server sanitizes the strings, saves the sighting, and returns it with HTTP `201`. |
| `GET /api/news` | Streams news updates as Server-Sent Events. |
