# Arya's portfolio

A basic portfolio in `public/index.html`. Plain HTML, with browser default styling. No CSS, JavaScript, React, dependencies, or build step.

Published on Cloudflare: https://arya-portfolio.runtime-9f4e8d2c.workers.dev/

Domain: https://aryabuilds.online/ (also https://www.aryabuilds.online/).

Source: https://github.com/aryagupta-tech/Portfolio-Website/tree/main

The published page has been verified to match `public/index.html` exactly. The initial deployment used Cloudflare's static-file upload in the dashboard.

Edit `public/index.html` to change the bio, projects, and contact section. Project summaries are based on the public READMEs in [aryagupta-tech's GitHub repositories](https://github.com/aryagupta-tech?tab=repositories). The contact email is `aaryagupta.vns@gmail.com`.

## Preview

Open `public/index.html` in a browser, or run this from the project directory:

```sh
python3 -m http.server 8787 --bind 127.0.0.1 --directory public
```

Then visit http://127.0.0.1:8787.

## Publish on Cloudflare

`wrangler.jsonc` configures Cloudflare Workers to serve only `public/` on `aryabuilds.online/*` and `www.aryabuilds.online/*`.

The domain was added to Cloudflare's Free plan, and these nameservers were saved at GoDaddy:

```text
tani.ns.cloudflare.com
yadiel.ns.cloudflare.com
```

The existing DNS records were imported. Worker routes serve the portfolio through the proxied root and `www` records. The registry delegates to Cloudflare, and the zone and Universal SSL certificate are active.

To publish later edits with Wrangler:

1. Make sure you own `aryabuilds.online` and that its zone is active in your Cloudflare account.
2. Sign in through Wrangler:

   ```sh
   npx wrangler@latest login
   ```

3. Deploy from this directory:

   ```sh
   npx wrangler@latest deploy
   ```

You can also upload the updated `public/index.html` through the existing `arya-portfolio` Worker's **New deployment** action in the Cloudflare dashboard. Domain HTTPS is provided by Cloudflare once the zone is active.

References: [Static assets](https://developers.cloudflare.com/workers/static-assets/get-started/) · [Worker routes](https://developers.cloudflare.com/workers/configuration/routing/routes/)
