# Datawrapper List Image Exporter

Load a published Datawrapper chart, crop it or remove gaps, and export a 1920 × 1080 PNG. The chart-finder bookmarklet finds charts on a Cato article and opens them in the resizer.

## Project structure

```text
index.html                       Main page, styles, and JavaScript
.github/workflows/pages.yml      GitHub Pages deployment
```

`index.html` was previously named `v2-bookmarklet.html`. It contains the app's HTML, CSS, and JavaScript. There is no build step or package installation. The page loads Basecoat CSS from jsDelivr and chart images from Datawrapper.

The local `archive/` folder holds earlier prototypes and is ignored by Git. Older commits may still contain those files.

## GitHub Pages deployment

1. In the repository's **Settings → Pages → Build and deployment**, select **GitHub Actions** as the source.
2. Commit and push these changes to `main`. The **Deploy GitHub Pages** workflow publishes the site on each push to `main`; it can also be run manually from the Actions tab.
3. Open <https://catoinstitute.github.io/datawrapper-list-image-exporter/> after the deployment succeeds.

The workflow uploads only `index.html`, so repository documentation and local archives are not included in the deployed site. Reinstall the chart-finder bookmarklet from the deployed page so it opens the public address.

## Local preview

From the repository root, run:

```sh
python3 -m http.server 5500
```

Open <http://localhost:5500/>. To load a chart through the URL, append `?id=CHART_ID` and replace `CHART_ID` with its five-character Datawrapper ID. Add `&plain=1` to load the version without the title, notes, or sources.

Drag the chart-finder bookmarklet onto your bookmarks bar. Open a Cato article with Datawrapper charts and click the bookmarklet.

The bookmarklet saves the resizer's address when you install it. Reinstall it from the published site after deployment or a change to the site's address.

## Editing and checking changes

Edit the app in `index.html`. The `BOOKMARKLET_SRC` template in its inline script contains the chart-finder code. The page sets the bookmarklet's resizer links to its own URL.

After editing, preview locally and check that you can:

- Load a chart and switch to its plain version.
- Crop the chart and remove a gap.
- Download the PNG.
- Run the finder on a Cato article and open a chart at the correct resizer address.
