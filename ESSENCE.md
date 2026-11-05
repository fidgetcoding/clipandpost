# clip&post: the essence

**Live: <https://clipandpost.lorecraft.io>**

**What it is.** The one-page site for clip&post, my short-form clipping agency. We take a creator's long videos, cut them into highly edited shorts, and post them every day across 50+ secondary accounts on TikTok, Reels, Shorts, X and Facebook. The page sells that: a tilted wall of creator tiles that races in when it opens, the client roster with real audience sizes, how it works, two plans, an FAQ, and one booking button that goes straight to my calendar.

**Who it's for.** Creators and brands who want more reach out of what they've already filmed. On the code side, anyone who wants a fast one-page site to fork: plain HTML, CSS and JS, every word in one file, nothing to build.

**Why it exists.** It started small. I wanted one creator's card off the site for a while, and when I went to do it, the site wasn't where I thought. The .com pointed at a site builder I'd stopped paying for and showed a dead "not available" page. The only working copy sat on another builder's subdomain, and there was no source repo anywhere. So I cloned my own old build, moved it to my own domain, and then redesigned it, because it looked like every other AI-built landing page.

**What's different.**

- The tilted wall. 9:16 creator tiles on a tilted 3D plane burst in on open and speed up as you scroll.
- Proof up front. All 19 creators show with their audience sizes, each linking to their channel.
- One button that matters. Every "Book a Call" and "Get a Quote" opens my booking page in a new tab.
- Nothing to build. It's one HTML file plus one content file, `site/kit/content.js`. Change the copy, the creators or the booking link there and the page follows.
- It runs on my own subdomain as a Cloudflare Worker with static assets, off the builders for good.
- It was designed in labs, not in one shot: 20 directions, 20 refinements of the three I liked, a merge of my two favourites, then 54 logo options.

**How to try it.** Open the live link above. To run your own copy:

```bash
git clone https://github.com/fidgetcoding/clipandpost.git
cd clipandpost/site
python3 -m http.server 8000
```

Open <http://localhost:8000>. Deploying to your own domain is two steps, both in the [README](README.md).

**What works today.**

- The live page matches this repo byte for byte. On November 5, 2026, I fetched the live `index.html` and `kit/content.js` and compared them to `main`: identical. The page, the content file, the favicon and the booking link all returned 200.
- After the redesign shipped and again after the new logo (November 2), a Playwright check of the live site at 1440 px and 390 px wide passed: 6 of 6 booking buttons open my booking page in a new tab, 19 of 19 creator links work, all 11 sections are there, the FAQ opens, with no broken images, no sideways scroll and no console errors.
- Before the redesign, the clone matched the old site side by side in full-page screenshots, apart from the card I took off and the builder's badge.
- There's no CI, because there's nothing to build. The checks above are the test record, and [EVOLUTION.md](EVOLUTION.md) has each one.
