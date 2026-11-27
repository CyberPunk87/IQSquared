# AI Second Brain (PWA)

No build step. Plain HTML, CSS and JS. Files: `index.html`, `manifest.json`, `sw.js`, `icon.svg`, `icon-*.png`.

## Run locally
```
cd second-brain
python3 -m http.server 8080      # or: npx serve .
```
Open http://localhost:8080. Service workers only run on `localhost` or HTTPS, so opening `index.html` by double-click will work as a page but not as an installable app.

## Test on your phone
Phone and computer on the same Wi-Fi: open `http://<computer-ip>:8080`. Installing requires HTTPS, so deploy (below) for the real thing.

## Deploy (free, HTTPS)
Drag the `second-brain` folder into Netlify Drop or Cloudflare Pages, or push it to a GitHub repo and enable GitHub Pages.

## Add to Home Screen
- iPhone: Safari, Share, Add to Home Screen.
- Android: Chrome menu, Install app.

## Data and backups
Notes are stored in IndexedDB on that device and origin. A phone install and a desktop install do not sync. Use Import, Export JSON to move or back up, and Restore from JSON on the other device. Clearing site data deletes the vault.

## Using it
- Notes: Markdown with `[[wikilinks]]`, `#tags`, backlinks. Links to missing notes show dashed and create the note on tap.
- Graph: drag to pan, pinch or scroll to zoom, tap a node to select and open. Search accepts `#tag`.
- Think: regenerates `Opportunities & Trends` (Trends, Opportunities ranked by leverage, How this feeds action, Connections) and adds new items to the Growth Action List.
- Actions: tap the status button to cycle todo, doing, done. Statuses sync into the `Growth Action List` note.
- Import: paste several notes (each begins with `# Title`) or upload `.md` files.

## Synthesis modes
- Local (default): finds notes that several sources link to, and action-worded lines in source notes. It does not rewrite or infer.
- Claude: paste an Anthropic API key under Import. Synthesis then calls the Anthropic API directly from your browser, with all source notes sent as input. The key stays in local storage on your device, so use this only on devices you trust, or route calls through your own backend before sharing the app.

## Limits
The graph layout is O(n²), comfortable to roughly 500 nodes.
