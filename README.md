# clip&post

**The site for clip&post, my short-form clipping agency. Let's go viral.**

### 👉 Live: [clipandpost.lorecraft.io](https://clipandpost.lorecraft.io)

Short version: [ESSENCE.md](ESSENCE.md). How it got built: [EVOLUTION.md](EVOLUTION.md).

---

## What it is

clip&post takes a creator's long-form content, cuts it into highly edited shorts, and posts them every day across 50+ secondary accounts on TikTok, Reels, Shorts, X and Facebook. The views pile up, and the followers find their way back to the main channel. It's been 19 creators so far, from 5.69K to 25.3M followers, and more than a billion engagements.

This repo is the one-page site that sells it: a tilted wall of creator tiles that races in when the page opens, the client roster with real audience numbers, how it works, pricing, and a big "Book a Call" button that goes straight to my calendar.

## Why I made it

It started because I wanted one card off the old site, and found out the site was barely alive. The old version came out of an AI site builder and looked like every other AI-built landing page. It lived on two hosted builders, and the .com pointed at the one I'd stopped paying for, so it showed a dead page. I wanted it out of there, on my own domain, looking like a studio made it.

I cloned the old build exactly, moved it to Cloudflare, then ran design labs: 20 directions, then 20 refinements of the three I liked, then a merge of my two favourites. After that came 54 logo options, and I picked one. The full story is in [EVOLUTION.md](EVOLUTION.md).

## What's on the page

- **The tilted wall.** 9:16 creator tiles on a tilted 3D plane. They burst in on open and speed up as you scroll.
- **Real proof.** All 19 creators with their audience sizes, each linking to their channel.
- **The strategy.** 50+ secondary accounts, explained in one sentence and one diagram.
- **How it works, pricing, ideal client, FAQ.** Two plans (Basic and Expert), no contracts, cancel anytime.
- **One button that matters.** Every "Book a Call" and "Get a Quote" opens [book.morgen.so/lorecraft](https://book.morgen.so/lorecraft).
- **The wordmark.** Lowercase `clip&post` with the ampersand shrunk to lowercase height in rose. The favicon is `c&p`.

## Run it yourself

It's a static site, with no build step and no framework.

```bash
git clone https://github.com/fidgetcoding/clipandpost.git
cd clipandpost/site
python3 -m http.server 8000      # open http://localhost:8000
```

All the copy, creators and links live in one file: `site/kit/content.js`. Change them there and the page updates. Forking it? Change `bookUrl` in that file first, or your visitors will be booking calls on my calendar. The wordmark sits in `site/index.html`, in the nav and the footer.

## Deploy

It runs as a Cloudflare Worker with static assets (see `wrangler.jsonc`). To ship it on your own domain:

1. Change the `routes` pattern in `wrangler.jsonc` to your domain. The domain has to be on your Cloudflare account.
2. Run `npx wrangler@4 login`, then `npx wrangler@4 deploy` from the repo root.

## Stack

Plain HTML, CSS and JS. Fonts are Big Shoulders Display, Hanken Grotesk and IBM Plex Mono, with Phosphor icons. Hosting is Cloudflare Workers.

## License

MIT © Nate Davidovich. See [LICENSE](LICENSE).
