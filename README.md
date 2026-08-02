# Wedding invite

One static page, personalised per friend via the URL. No build step, no server.

`index.html?to=<name>&key=<key>` — e.g. `?to=paula&key=82595918`. Needs BOTH the
name and its matching key, otherwise the whole invite shows a "locked" screen so
people can't peek at someone else's gift just by guessing a name. The name drives:
- the **greeting** on the envelope ("FOR PAULA"), and
- their **scratch-card gift** (an interactive scratch-off, hidden until "Reveal your gift").

Names + keys + gifts live in `guests.js` (single source of truth, shared with `links.html`).

**Security caveat:** this is a static site, so `guests.js` is downloadable by anyone
who opens the browser dev tools. The key stops *casual* snooping (changing `?to=`);
it is NOT encryption. For a wedding among friends that's fine — flag it if you need
real privacy and we can encrypt each gift with its key instead.

## Stages

1. Envelope → tap to open
2. Card 1 — couple + date/venue (`cover-image.jpg`)
3. Card 2 — dress code, 3 photos (`1.jpg`, `2.jpg`, `3.jpeg`)
4. Card 3 — schedule + live countdown + "Reveal your gift" button
5. Card 4 — cartoon yellow scratch card; scratch the gold to reveal the gift

## Editing

- **Friends/gifts:** edit `guests.js`.
- **Wedding details:** the couple name, date, venue in `index.html` are still Canva
  placeholders ("AMARA & MARK", "123 Anywhere St"). Edit the text directly, and
  update `WEDDING_DATE` in the script if the countdown date changes.
- **Photos:** replace `cover-image.jpg` / `1.jpg` / `2.jpg` / `3.jpeg`. Note `1.jpg`
  (~5 MB) and `2.jpg` (~2.7 MB) are heavy for mobile — worth shrinking to ~1600px.

## Deploy (GitHub Pages)

Already live at https://rafal-mac.github.io/wedding-invite/ — just push:

```
git add . && git commit -m "update" && git push
```

Pages redeploys in ~1 min.

## Friend links

Open `links.html` in a browser — it lists all 15 personalised links with copy
buttons. Set the base URL once at the top if it ever changes.
