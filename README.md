# gen-story

The story page and the one pager of gen-system, as a static site on Cloudflare.

| Path | Page |
|---|---|
| `/` | The story (`public/index.html`) |
| `/short.html` | The one pager |
| `/vi/` | The story in Vietnamese |
| `/vi/short.html` | The one pager in Vietnamese |

Everything the site serves sits in `public/`. The pages need no build step. They load only Google
Fonts and link to GitHub.

## Deploy

The site deploys as a Cloudflare Worker with static assets and no Worker script, the same setup as
the learning plan site. `wrangler.jsonc` names it `gen-story` and points `assets.directory` at
`./public`.

**From the command line.** Run this in this folder:

```bash
npx wrangler deploy
```

The first run asks you to log in and creates the Worker.

**From GitHub.** Push this folder as its own repository. In the Cloudflare dashboard, open
Workers & Pages, create an application, import the repository, and keep the deploy command
`npx wrangler deploy`. Leave the build command empty.

Do not use `wrangler pages deploy`. This folder is set up for a Worker, not a Pages project.

Cloudflare serves `/short.html` at `/short` and redirects the old path, so every link in the pages
still works.

## Custom domain

In the Worker, open Settings, then Domains & Routes, and add your custom domain. Cloudflare creates the DNS record
when the domain uses Cloudflare DNS.

The `hreflang` links in the pages are root relative (`/`, `/vi/`, `/short.html`, `/vi/short.html`),
so they work on any domain.

`public/_headers` sets three security headers on every response.
