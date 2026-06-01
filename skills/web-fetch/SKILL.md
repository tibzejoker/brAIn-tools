---
name: web-fetch
description: Fetch a URL or hit an HTTP API from the network. Use when a task needs live web content, a REST call, or a webhook — anything that leaves the bus over HTTP.
---

# Fetching over HTTP

Route HTTP through the `http-bridge` node; don't try to reach the network any other way.

## Steps
1. Send the request to `http-bridge`: method, URL, and headers/body if needed.
2. Prefer GET for reads; only POST/PUT/DELETE when you intend to change remote state, and say what you're changing.
3. Read the response back off the bus before acting on it.

## Pitfalls
- Never put secrets or personal data in a URL query string.
- A non-200 is data, not a crash: surface the status + a short reason, don't pretend it succeeded.
- Large bodies cost tokens — ask for just what you need, summarise before reasoning over it.
