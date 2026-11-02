# AGENTS.md

Live site: **https://clipandpost.lorecraft.io**

## What this repo is
This is the static one-page site for Clip & Post, a short-form clipping agency. There's no build step and no framework.

## Layout
- `site/index.html`: the whole page (HTML, CSS, JS inline)
- `site/kit/content.js`: all copy, the 19 creators, and links (`window.KIT`). Edit content here, not in the HTML.
- `site/kit/img/`: creator avatars
- `site/favicon.*`, `site/apple-touch-icon.png`: the `c&p` icon
- `wrangler.jsonc`: Cloudflare Worker with static assets, SPA fallback, and the custom domain route

## Rules
- Every booking CTA must point to `KIT.bookUrl`, which is `https://book.morgen.so/lorecraft`.
- One page with 11 sections in this order: nav, hero, provide, clients, strategy, process, pricing, ideal, faq, cta, footer.
- The wordmark is `clip<span class="amp">&amp;</span>post` in Hanken Grotesk 800, with the & at 0.7em in rose `#e5195e`.

## Run and deploy
- Local: `cd site && python3 -m http.server 8000`
- Deploy: `npx wrangler@4 deploy` from the repo root (needs Cloudflare auth).
