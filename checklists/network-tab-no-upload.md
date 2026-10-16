# Prove a browser converter stays local (Network tab)

Use this when a site claims “no upload” / “runs in your browser.”

1. Open Chrome or Edge → DevTools → **Network**.
2. Start a conversion on the tool page.
3. Confirm you do **not** see the media file as a large **POST** to a third-party convert API.
4. Small JS / WASM / CSS requests are normal (the tool code loading).
5. The result download should come from the tab’s local result, not a remote job URL.

If you see a multi‑MB upload of your video to another host, treat it as an upload converter regardless of marketing copy.
