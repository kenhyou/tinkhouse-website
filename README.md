# tinkhouse.com

Company introduction page for **Tink House** — a Sydney-based company building AI agents for local small-business marketing.
The page is used to introduce the company (primarily to investors), so it focuses on mission, opportunity and what we're building rather than sales.

Plain static HTML/CSS with no build step, hosted on GitHub Pages.
The header and footer are repeated in each page's HTML — update all three pages when changing them.
Sub-pages use root-relative paths (`/assets/...`), so preview with a local server rather than opening the files directly.

## Structure

```
index.html            # home page (company intro for investors)
ai-training/          # AI training service page
marketing/            # marketing consulting & management page
404.html              # GitHub Pages not-found page
assets/css/style.css  # design tokens (colours, fonts) live in :root at the top
assets/js/main.js     # mobile menu, header border, footer year
assets/img/           # logo.png, favicon-32x32.png, apple-touch-icon.png, og-image.png (1200×630 link preview)
favicon.ico           # legacy favicon (browsers request /favicon.ico)
brand/                # original high-res logo artwork (source for the icons above)
CNAME                 # custom domain for GitHub Pages
robots.txt, sitemap.xml
```

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Before launch

- [ ] Make sure `contact@tinkhouse.com` receives mail (Google Workspace alias). It appears in `index.html` (hero button, contact section, JSON-LD).
- [ ] If the logo changes: replace `brand/tinkhouse-mark-source.png`, regenerate `assets/img/logo.png`, `favicon-32x32.png`, `apple-touch-icon.png` and `/favicon.ico`, then re-export `assets/img/og-image.png`.
- [ ] Add legal entity name / ABN to the footer once registered.

## Market figures

Every number on the page must cite a public source in the footer **Sources** list.
Current figures come from ASBFEO, *Number of small businesses in Australia* (Aug 2025), based on ABS *Counts of Australian Businesses*, June 2025:
2,656,469 small businesses (97.3% of all businesses); 64% self-employed / non-employing.
Re-check against the latest ABS release when updating.

## Deploy (GitHub Pages + custom domain)

1. Create a GitHub repository and push this folder to the `main` branch.
2. Repository **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main` / `(root)`.
3. The `CNAME` file already sets the custom domain to `www.tinkhouse.com`.
4. At the domain registrar, add DNS records:

   | Type  | Host  | Value                       |
   |-------|-------|-----------------------------|
   | CNAME | `www` | `<github-username>.github.io` |
   | A     | `@`   | `185.199.108.153`           |
   | A     | `@`   | `185.199.109.153`           |
   | A     | `@`   | `185.199.110.153`           |
   | A     | `@`   | `185.199.111.153`           |

5. GitHub **Settings → Pages → Verified domains** (account level): verify `tinkhouse.com` to prevent domain takeover.
6. Once DNS resolves, tick **Enforce HTTPS**. `tinkhouse.com` will redirect to `www.tinkhouse.com`.
