# v0.2.0 Announcement Posts

## Discord (htmx server)

just shipped v0.2.0 of htmx-devtools with full htmx 4.0 alpha support. the extension auto-detects which version you're running and adapts everything transparently. no config needed.

what's new:
- dual version support (2.x + 4.0 working simultaneously)
- request tracking via ctx objects for htmx 4 (since XHR is gone)
- synthetic error detection for HTTP 4xx/5xx (htmx 4 doesn't fire error events for these)
- LCS-based DOM diff in the swap visualizer
- request history per element in the elements tab
- version badge showing which htmx you're running (blue for 2.x, purple for 4.0)

live demos you can try right now without installing anything:
- htmx 2.x: https://atoolz.github.io/htmx-devtools/v2/
- htmx 4.0: https://atoolz.github.io/htmx-devtools/v4/

repo: https://github.com/atoolz/htmx-devtools

feedback welcome, especially from anyone already testing htmx 4 alpha

---

## Reddit (r/htmx)

**Title:** HTMX DevTools v0.2.0 - now with htmx 4.0 alpha support

Just released v0.2.0 of the HTMX DevTools browser extension. The big addition is full htmx 4.0 alpha support alongside the existing 2.x support. The extension auto-detects which version is running and adapts transparently.

**What changed in v0.2.0:**

htmx 4.0 is a ground-up rewrite that replaces XHR with fetch(), changes all event names to colon-namespaced format, and merges all error events into a single `htmx:error`. The devtools now handles all of this:

- Canonical event mapping layer that normalizes both 2.x and 4.0 event names
- Request tracking via ctx WeakMap for htmx 4 (replaces XHR tracking)
- Synthetic HTTP error detection for 4xx/5xx responses (htmx 4 swaps these by default without firing error events)
- Support for new htmx 4 attributes (hx-action, hx-method, hx-config, hx-status)
- Version badge in the panel (blue for 2.x, purple for 4.0)

**Other improvements:**

- LCS-based DOM diff algorithm in the Swap Visualizer (replaces the naive set-based diff)
- Request history per element in the Element Inspector (click to jump to Requests tab)
- Element tree auto-refreshes in real time with debounced event subscription
- Per-tab search filters (no longer shared between tabs)
- Better serialization handling for htmx 4 detail objects (Response, Headers, ctx)

**Try it without installing:**

- htmx 2.x demo: https://atoolz.github.io/htmx-devtools/v2/
- htmx 4.0 demo: https://atoolz.github.io/htmx-devtools/v4/

Both demos use client-side mock servers so everything works in the browser.

**Install from source:**

```
git clone https://github.com/atoolz/htmx-devtools.git
cd htmx-devtools && npm install && npm run build:chrome
```

Then load `dist/` as unpacked extension in chrome://extensions.

GitHub: https://github.com/atoolz/htmx-devtools

Looking for feedback from anyone testing htmx 4 alpha. What's missing? What would make this more useful?

---

## Twitter/X

htmx-devtools v0.2.0: now works with htmx 4.0 alpha

auto-detects 2.x vs 4.0, adapts transparently. no config needed.

new: ctx-based request tracking (XHR is gone in 4.0), synthetic HTTP error detection, LCS DOM diffs, per-element request history, version badge

try it: https://atoolz.github.io/htmx-devtools/v4/
repo: https://github.com/atoolz/htmx-devtools
