# Launch Posts

## Reddit (r/htmx)

**Title:** I built a browser DevTools extension for debugging HTMX applications

Built an open-source Chrome/Firefox DevTools extension that adds an "HTMX" tab to your browser's developer tools. It captures the full request lifecycle, shows a live DOM tree of htmx elements, has an event timeline with filters, a swap diff visualizer, and surfaces silent errors.

Features:
- Request Inspector with timing breakdown (config > send > wait > swap > settle)
- Element Inspector with collapsible DOM tree, hover highlight, and element picker
- Event Timeline with category filters (init, request, xhr, response, swap, oob, history, error)
- Swap Visualizer with before/after diff
- Error Panel that catches silent failures (targetNotFound, swapError, responseError, timeout)

The extension works by injecting a page script that listens to all htmx:* events and serializes the data through a message pipeline to the DevTools panel (built with Preact).

GitHub: https://github.com/atoolz/htmx-devtools
Live demo (no install needed): https://atoolz.github.io/htmx-devtools/

Looking for feedback from the community before publishing to the Chrome Web Store. What features would you want to see?

---

## Hacker News

**Title:** Show HN: HTMX DevTools - Browser extension for debugging HTMX apps

HTMX has minimal built-in debugging (htmx.logAll() and a debug extension that floods the console). I built a proper DevTools extension that adds an "HTMX" tab with 5 panels:

1. Request Inspector - captures the full htmx request lifecycle with timing, headers, body, and event correlation
2. Element Inspector - live DOM tree showing only htmx-relevant nodes with attribute resolution and hover highlighting
3. Event Timeline - filterable list of all htmx events color-coded by category
4. Swap Visualizer - records DOM snapshots before/after swaps with line-by-line diff
5. Error Panel - surfaces silent failures that htmx swallows (target not found, swap errors, response errors)

Architecture: page script (MAIN world) captures events > content script relays > background service worker tracks state > Preact panel renders. All built with TypeScript + Vite, ~50KB panel.

GitHub: https://github.com/atoolz/htmx-devtools
Live demo: https://atoolz.github.io/htmx-devtools/

---

## Twitter/X

Built an open-source DevTools extension for @htmx_org

Adds an "HTMX" tab to Chrome/Firefox DevTools with:
- Request inspector with timing breakdown
- Live DOM tree of htmx elements
- Event timeline with category filters
- Swap diff visualizer
- Silent error detection

No more console.log debugging.

https://github.com/atoolz/htmx-devtools

---

## Discord (htmx server)

Hey! I built a browser DevTools extension for debugging HTMX apps. It adds an "HTMX" tab to Chrome/Firefox DevTools with request inspection, a live element tree, event timeline, swap diffs, and error detection.

It's open source and I'm looking for feedback before publishing to the Chrome Web Store.

**GitHub:** https://github.com/atoolz/htmx-devtools
**Live demo (no server needed):** https://atoolz.github.io/htmx-devtools/

Would love to hear what you think and what features you'd want to see. PRs welcome too.
