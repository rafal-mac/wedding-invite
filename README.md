# Wedding invite

One static page, personalised per friend via the URL. No build step, no server.

- **Name** comes from `?to=` — shows "FOR SARAH" on the envelope.
- **Scratch card link** comes from `?card=` — sets the "Scratch Card" button. No `card` = button hidden.

Example: `.../index.html?to=Sarah&card=https://scratch-provider.com/abc123`

## 1. Add the photos

Drop 7 files into an `images/` folder next to `index.html`:

- `couple.jpg` — the couple photo (card 1)
- `dresscode-1.jpg` … `dresscode-6.jpg` — the dress-code gallery (card 2)

(The original Canva `canva://` images only work inside Canva, so they've been swapped for these local paths.)

## 2. Edit the wedding details

The couple name, date, venue and address in `index.html` are still the Canva
placeholders ("AMARA & MARK", "123 Anywhere St, Any City"). Edit the text
directly. Also update `WEDDING_DATE` in the script if the countdown date changes.

## 3. Deploy to GitHub Pages

1. `git init && git add . && git commit -m "wedding invite"`
2. Create a repo on GitHub, push to it.
3. Repo → Settings → Pages → Source: `main` branch, `/ (root)` → Save.
4. Your invite is live at `https://YOURNAME.github.io/REPO/`.

## 4. Make a link per friend

Open `links.html` in your browser. Set the base URL to your Pages address once,
then paste each friend's name + scratch link and copy the generated URL.
