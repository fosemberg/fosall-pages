# fosall-pages

Published build of [**FosMeet**](https://github.com/fosemberg/fosall) — one-to-one
video calls that connect two phones directly, peer to peer, with no server in
the middle.

**Live app: [fosemberg.github.io/fosall-pages/](https://fosemberg.github.io/fosall-pages/)**

## What is in here

Everything in `docs/` is build output. It is generated from the sources in
[`fosemberg/fosall`](https://github.com/fosemberg/fosall) and should never be
edited here — the next build overwrites it.

```
docs/
├── index.html              the app shell
├── 404.html                a copy of the shell, so deep links land somewhere
├── assets/                 content-hashed JavaScript and CSS
├── sw.js                   service worker: the app runs offline once installed
├── manifest.webmanifest    installable as a home-screen app
├── icon-*.png, icon.svg    app icons
└── .nojekyll               stops Pages from running the output through Jekyll
```

## Updating it

From a checkout of the source repository, with this repository checked out
alongside it:

```bash
cd fosall
npm install
npm run build:pages          # writes ../fosall-pages/docs
```

Then commit and push from here. Pass a path if the two repositories are not
siblings:

```bash
npm run build:pages -- /path/to/fosall-pages
```

## Enabling GitHub Pages

In this repository: **Settings → Pages → Source: Deploy from a branch**, branch
`main`, folder `/docs`.

Pages serves over HTTPS, which is what the app needs: browsers only grant
camera access on a secure origin.

## Privacy

The app is static. Nothing here receives your calls — audio, video and chat go
directly between the two browsers, and the invite payload travels in the URL
fragment, which is never sent to a web server. See the
[source repository](https://github.com/fosemberg/fosall) for the details.
