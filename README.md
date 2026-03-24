# </> HTMX DevTools

Browser DevTools extension for debugging [HTMX](https://htmx.org) applications. Inspect requests, elements, events, swaps, and errors in real time.

![Requests Tab](docs/screenshots/requests.png)

## Features

### Request Inspector
Capture the full HTMX request lifecycle with timing breakdown, headers, request/response body, and event trace.

- HTTP verb, URL, status, swap strategy
- Trigger and target element identification
- Visual timeline bar (Config > Send > Wait > Swap > Settle)
- HX-* request and response headers
- Record/pause/clear controls

![Request Inspector](docs/screenshots/requests.png)

### Element Inspector
Live DOM tree showing all HTMX elements with their hierarchy, attributes, and resolved targets. Updates in real time as the page changes.

- Collapsible DOM tree filtered to HTMX-relevant nodes
- Click to inspect: shows hx-* attributes, resolved targets, internal data
- Element picker: click any element on the page to inspect it
- Hover highlighting on the inspected page

![Element Inspector](docs/screenshots/elements.png)

### Event Timeline
Filterable timeline of all HTMX events with category color coding and expandable detail payloads.

- Category filters: Init, Request, XHR, Response, Swap, OOB, History, Transition, Error
- Timestamps relative to first event
- Click to expand full `event.detail` JSON
- Request correlation (linked request ID)

![Event Timeline](docs/screenshots/timeline.png)
![Event Detail](docs/screenshots/timeline-detail.png)

### Swap Visualizer
Record DOM swaps with before/after snapshots and diff view.

- Record/pause controls
- Response HTML view
- Before/After DOM snapshots
- Line-by-line diff with add/remove highlighting
- Swap strategy and target element info

![Swap Visualizer](docs/screenshots/swaps.png)

### Error Panel
Surface silent HTMX failures grouped by error type with badge counts.

- Response errors (4xx, 5xx)
- Target not found errors
- Network timeouts
- Swap errors
- Click to jump to associated request

![Error Panel](docs/screenshots/errors.png)

## Installation

### From source (development)

```bash
git clone https://github.com/atoolz/htmx-devtools.git
cd htmx-devtools
npm install
npm run build:chrome
```

#### Chrome / Edge / Brave / Arc
1. Open `chrome://extensions`
2. Enable "Developer mode"
3. Click "Load unpacked"
4. Select the `dist/` folder

#### Firefox
```bash
npm run build:firefox
```
1. Open `about:debugging#/runtime/this-firefox`
2. Click "Load Temporary Add-on"
3. Select `dist/manifest.json`

## How it works

The extension uses a 4-layer architecture:

```
Page Script          Content Script       Service Worker       DevTools Panel
(MAIN world)         (isolated)           (background)         (Preact UI)

Captures htmx    ->  Relays via        -> Routes messages,  -> Renders 5 tabs
events on            postMessage +         maintains state      with real-time
document             runtime.sendMessage   per tab              updates
```

- **Page Script** runs in the page's JS context via `"world": "MAIN"` content script. Listens to all `htmx:*` events, serializes element data, and batches messages.
- **Content Script** bridges page context and extension context via `window.postMessage` and `chrome.runtime.sendMessage`.
- **Background Service Worker** manages per-tab state, tracks request lifecycles, and routes data to the panel.
- **Panel** is a Preact + Signals app rendered inside `chrome.devtools.panels.create()`.

## Development

```bash
npm run dev          # Watch mode (rebuilds on changes)
npm run build        # Production build
npm run build:chrome # Build + copy Chrome manifest
npm run build:firefox # Build + copy Firefox manifest
npm run typecheck    # TypeScript check
npm run test         # Run tests
```

### Test page

A test server with all HTMX features is included:

```bash
node test/e2e/fixtures/test-server.js
```

Open `http://localhost:3456` to test all features: GET/POST/PUT/DELETE requests, error scenarios (404, 500, timeout), swap strategies, OOB swaps, polling, search with delay, contact editor (click-to-edit pattern), and todo list.

## Tech stack

- **TypeScript** + **Vite** (multi-entry build with IIFE outputs)
- **Preact** + **@preact/signals** (3KB panel UI)
- **Chrome Manifest V3** (also compatible with Firefox MV3 128+)

## License

MIT
