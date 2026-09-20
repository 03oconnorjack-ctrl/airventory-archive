# The Archive site

Static site: `archive/index.html` lists the brands, `archive/<brand>/index.html` is the grid
with lightbox and arrow keys, `archive/<brand>/manifest.json` lists every image with its
pixel size, `archive/<brand>/<file>.jpg` is the original at original size, `thumb/` is a 300px
copy for the grid. 126MB, four brands, 2,669 images. No build step.

## Publish (one command, needs Jack because it creates a public repo)

```bash
cd ~/Documents/claude-mac-move/maverick-marketing/research/archive-site && gh repo create airventory-archive --public --source=. --push && gh api -X POST repos/03oconnorjack-ctrl/airventory-archive/pages -f build_type=legacy -f 'source[branch]=main' -f 'source[path]=/'
```

Live about a minute later at `https://03oconnorjack-ctrl.github.io/airventory-archive/archive/abercrombie/`.

## Framer

Code component `ArchiveGallery.tsx` is in the Airventory Web project (branch "supple-lagoon",
draft page `/archive`). It fetches `manifestUrl` and renders the same grid and lightbox, so the
images never touch Framer. Merge the branch and undraft the page once the GitHub Pages URL
is live. To put it on `airventory.io/archive` directly, that is the component; to use a
subdomain instead, add a CNAME `archive.airventory.io` to `03oconnorjack-ctrl.github.io` at
Hostinger and a `CNAME` file in this repo.

## Adding a brand

Drop a folder of `{year}_{id}_{colour}.jpg` files, run the manifest script
(`airventory-marketing` session scratchpad, `archive/site` build step: originals copied,
300px thumbs, manifest.json), add one card to `archive/index.html`, commit, push.
