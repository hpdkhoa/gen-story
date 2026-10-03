# gen-story

The story page and the one pager of gen-system, as a static site for Cloudflare Pages.

| Path | Page |
|---|---|
| `/` | The story (`public/index.html`) |
| `/short.html` | The one pager |
| `/vi/` | The story in Vietnamese |
| `/vi/short.html` | The one pager in Vietnamese |

Everything the site serves sits in `public/`. The pages need no build step. They load only Google
Fonts and link to GitHub.

## Deploy

Pick one.

**From the command line.** Run this in this folder:

```bash
npx wrangler pages deploy
```

`wrangler.toml` names the project `gen-story` and points it at `public/`. The first run asks you to
log in and creates the project.

**From GitHub.** Push this folder as its own repository. In the Cloudflare dashboard, open
Workers & Pages, create a Pages project, connect the repository, leave the build command empty and
set the build output directory to `public`.

**By upload.** In the dashboard, create a Pages project with Direct Upload and drop the `public`
folder in.

## Custom domain

In the Pages project, open Custom domains and add your domain. Cloudflare creates the DNS record
when the domain uses Cloudflare DNS.

The `hreflang` links in the pages are root relative (`/`, `/vi/`, `/short.html`, `/vi/short.html`),
so they work on any domain.

`public/_headers` sets three security headers on every response.
