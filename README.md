# prettyapps.co

The marketing site for **Pretty Apps** and our meditation timer, **Pause Point**.
Pure static HTML + CSS, no build step, hosted on GitHub Pages under the custom
domain `prettyapps.co`.

## What's in here

| File | Purpose |
| --- | --- |
| `index.html` | Home page / Pause Point product page |
| `privacy.html` | Privacy Policy for Pause Point |
| `404.html` | Not-found page (GitHub Pages serves this automatically) |
| `styles.css` | The single shared stylesheet |
| `assets/icon.svg` | App icon (used as the logo mark) |
| `assets/favicon.svg` | Favicon |
| `assets/apple-touch-icon.png` | 180×180 icon for iOS home-screen bookmarks |
| `assets/og-image.png` | 1200×630 social preview image |
| `CNAME` | Tells GitHub Pages the custom domain (`prettyapps.co`) |
| `.nojekyll` | Disables Jekyll processing so files are served as-is |

## Editing

Open any `.html` file and edit it; there is nothing to compile. Preview locally
with any static server, for example:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

### Swapping in the real App Store link

When Pause Point is live, edit `index.html` and change the one `href` on the
element with `id="app-store-link"` from `#` to the App Store URL, and delete
its `aria-disabled="true"` attribute. Optionally update the two "Coming soon"
labels in the hero and the Early birds section.

## One-time setup: GitHub Pages + custom domain

### 1. Enable GitHub Pages (in this repository's settings)

1. Go to **Settings → Pages** (`https://github.com/prettyapps-co/prettyapps.co/settings/pages`).
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Under **Branch**, pick `main` and the `/ (root)` folder, then click **Save**.
4. Under **Custom domain**, enter `prettyapps.co` and click **Save**.
   The `CNAME` file in this repo already contains `prettyapps.co`, so GitHub
   will keep the two in sync.
5. After the DNS records below have propagated and GitHub shows a green
   "DNS check successful", tick **Enforce HTTPS**. GitHub provisions the
   certificate automatically; this can take up to an hour after the DNS check
   passes.

### 2. DNS records (at your domain registrar)

Add these records for `prettyapps.co`. The A/AAAA records point the apex
domain at GitHub Pages; the CNAME lets `www.prettyapps.co` redirect to the
apex.

| Type | Host / Name | Value | TTL |
| --- | --- | --- | --- |
| A | `@` | `185.199.108.153` | 3600 |
| A | `@` | `185.199.109.153` | 3600 |
| A | `@` | `185.199.110.153` | 3600 |
| A | `@` | `185.199.111.153` | 3600 |
| AAAA | `@` | `2606:50c0:8000::153` | 3600 |
| AAAA | `@` | `2606:50c0:8001::153` | 3600 |
| AAAA | `@` | `2606:50c0:8002::153` | 3600 |
| AAAA | `@` | `2606:50c0:8003::153` | 3600 |
| CNAME | `www` | `prettyapps-co.github.io` | 3600 |

Notes:

- Remove any old A, AAAA, or ALIAS/ANAME records for `@` that pointed at the
  previous host before adding these.
- If your registrar does not accept `@`, use an empty name or the bare domain.
- Some registrars show the CNAME value with a trailing dot
  (`prettyapps-co.github.io.`); either form is fine.
- Verify with `dig prettyapps.co +noall +answer` and
  `dig www.prettyapps.co +noall +answer` once propagated.

### 3. (Recommended) Verify the domain for the organization

To stop anyone else from claiming `prettyapps.co` on GitHub Pages, verify it
under the organization: **Organization settings → Pages → Add a domain**, then
add the `TXT` record GitHub shows you (`_github-pages-challenge-prettyapps-co`)
at the registrar.

## License

© Pretty Apps. All rights reserved.
