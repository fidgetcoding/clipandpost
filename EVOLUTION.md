# How clip&post got built

My words are quoted as I typed them, typos fixed, nothing else. Commit hashes are from this repo. "Private note" means a dated record I keep offline. Times are Abu Dhabi time (UTC+4), where I was that day.

Live: **[clipandpost.lorecraft.io](https://clipandpost.lorecraft.io)**

## 1. The short version

All of it happened on one day, November 2, 2026. I wanted one creator's card off my agency's site for a while, and found out the site was barely alive. The .com showed a dead page from a builder I'd stopped paying for, and the only working copy sat on another builder with no source anywhere.

So I cloned it exactly, took the card off, and put it on Cloudflare at clipandpost.lorecraft.io. Then I redesigned it in three lab rounds: 20 directions, 20 refinements, and a merge of my two favourites. The logo got its own lab, 54 options. By about 8 PM the new site, wordmark and favicon were live, the repo was public, and the live checks passed at desktop and phone width.

## 2. Origin, in my words

The plan, once I knew the site had no home: "clone it exactly so it looks identical, and make a cloudflare link", and "keep everything else IDENTICAL".

Then, while the clone was going up, the bigger ask: a redesign that's "much sexier and less vibe coded". It "should still be one pager for all", with "all same sections and functions overall".

Shipping it: "lock it in, push live, make sure buttons work and the right calendar links are in it."

And the last piece: "only thing i dont like is logo."

## 3. Timeline

All on 2026-11-02.

| Time | What happened | Evidence |
|---|---|---|
| Afternoon | The ask: one creator's card off the site. The .com is dead and no source exists anywhere | Private note |
| 17:37 | The old build mirrored, untouched | `be1d7b6` |
| 17:43 | Card removed, builder scripts and badge stripped, Cloudflare Worker config. Live at clipandpost.lorecraft.io, and my lorecraft.io case study points here | `666f133`, private note |
| About 18:25 | Lab round 1: 20 directions in 5 families, three picks | Private note |
| 18:52 | Lab round 2 half built: 20 refinements, after a restart on a spend limit | Private note |
| 19:19 | Round 3 merge shipped: Tilted Plane on top, Tilted Floor below, every button on my booking page | `65f4978` |
| 19:57 | Logo lab (54 options), x-height wordmark, c&p favicon, README, build history, AGENTS, MIT license. Repo public | `255703e` |
| Nov 5 | Live page checked against `main`: identical | My run, `curl` |

## 4. Round by round

### Round 1: the rescue (to 17:43)

- **Found:** the .com pointed at a builder I'd stopped paying for, so it showed "this app isn't available yet". The only working copy was an old build on a hosted builder subdomain. There was no source repo on my disk or in any of the five GitHub orgs I checked.
- **Built:** an exact mirror of the built site, 25 files (HTML, JS, CSS, 19 avatars, favicon, robots), pulled down by a small crawler and committed untouched (`be1d7b6`). Then three edits: the card came off (its entry, its image reference and the image file), the builder's analytics scripts went (they'd break off the builder's servers), and so did its "Edit with…" badge. A Cloudflare Worker config with a custom domain route went in with them (`666f133`).
- **Tested:** full-page screenshots, original next to clone: identical apart from the card and the badge. Live, the page returned 200, the bundle had zero matches for the removed card, and the single-page fallback worked.
- **Broke:** my Mac's DNS cached the new subdomain as missing for a while, so the live checks went through Cloudflare's own resolver.
- **Fixed:** the case-study link on lorecraft.io now points here.
- **Wanted next:** "much sexier and less vibe coded".

### Round 2: lab round 1, 20 directions (to about 18:25)

- **Built:** a content kit from the live site's real copy, real creators and real links, then 20 options in 5 families:

| Family | Options |
|---|---|
| Editorial | Cover Story, Broadsheet, The Spread, Contents Page |
| Numbers | Scoreboard, Quote Board, Big Numerals, Broadcast |
| Feed | Reel Wall, Edit Timeline, Swipe Feed, Burned-in Captions |
| Poster | Swiss Red, Headliner, Field Tiles, Cut & Tape |
| Studio | Salon, Ledger, Orbit, Monograph |

- **Tested:** every option screenshot-checked at desktop and phone width: all 11 sections present, a working FAQ, no sideways scroll. The grid loaded all 20 with zero errors.
- **Picked:**
  - **Reel Wall:** "i love this one the sliding tiles right on opening is great"
  - **Field Tiles:** "i love how punchy the lets go viral at the top is, some of the things i dont like as much"
  - **Big Numerals:** "i love how clean this one is."
- **Wanted next:** motion on open, an oversized punchy headline, and a clean structure below the fold.

### Round 3: 20 refinements (about 18:30 to 19:00)

- **Built:** four families. Reel Wall+ (4) pushed how the wall moves. Punch+ (4) kept the Field Tiles headline and calmed the page under it. Clean+ (4) sharpened the numerals look. Hybrids (8) mixed all three in different amounts. The toy-like shape sections from Field Tiles were dropped as the likely part I didn't like.
- **Broke:** the first launch died when I hit my monthly spend limit. I switched to promotional credits and all four batches started over.
- **Tested:** the grid loaded all 20 with zero errors.
- **Picked:** "picked my two faves kill the others". Both came from one idea, a tilted 3D tile wall: **Tilted Plane** (Reel Wall+) and **Tilted Floor** (Hybrids).
- **Wanted next:** "i like tilted plane for the opening and until our proven strategy, after that i like tilted floor"

### Round 4: the merge (to 19:19)

- **Built:** Tilted Plane's top half, untouched. Tilted Floor's bottom layouts (big-numeral steps, a light Basic card next to a dark Expert card, a 2×2 Ideal Client grid, a split FAQ, a rose call-to-action band) moved onto the top half's palette and type: rose `#e5195e`, warm white, Big Shoulders, Hanken Grotesk and IBM Plex Mono. A pair of crossing scroll ribbons stitches the two halves together. Duplicate strategy sections from the floor half came out, and anchors got a 64px offset so the nav doesn't cover headings.
- **Broke:** the old site's buttons booked calls on the wrong calendar. "they both link to the wrong calendar. make sure its my morgen link"
- **Fixed:** every button now goes to [book.morgen.so/lorecraft](https://book.morgen.so/lorecraft), and the old link has zero hits in the code.
- **Tested:** Playwright, locally and then live, at 1440 px and 390 px: 6 of 6 booking buttons open my booking page in a new tab, 19 of 19 creator links work, all 11 sections are there, the FAQ opens, zero broken images, zero sideways scroll, zero console errors, zero failed requests.
- **Kept as is:** "Frequently Asked Questions" wraps to three lines in its narrow column. I looked at it and approved it.
- **Shipped:** `65f4978`.
- **Wanted next:** "only thing i dont like is logo"

### Round 5: the logo, and going public (to 19:57)

- **Built:** a wordmark lab with 54 options, 9 ideas × 6 versions, each shown big on a sheet and inside the real nav:

| Idea | Options |
|---|---|
| Ampersand | Hinge, Staircase, Hero Ampersand, Superscript, Ribbon, **x-height** |
| Cut | Razor, Bevel Cut, Shared P, Playhead, Trim Marks, Lifted Clip |
| Monogram | Interlock, Expanded Initials, Compass, Nested, Pixel, One Stroke |
| Stacked | Spine, Rule &, Stair, Plate, Shared P, Heavy/Light |
| Frame | Frame I, Twin Frames, Contact Strip, Screen Type, Deck, Reframe |
| Play | Play Counter, Upload T, Then Play, Loop C, Play P, Playhead |
| Display | Staple, Stencil Cut, Corner Trim, Step Up, Lockstep, Kerbline |
| Tilted | Floor, Ramp, Fold, Shuffle, Accelerate, Oblique Slab |
| Tape | Label Maker, Taped Join, Hang Tag, Die-Cut, Ticket Stub, Leader Strip |

- **Broke:** two of the designer agents shared a scratch folder, and one ran the other's generator script. Once the nav got the new wordmark, the pill's spacing pushed the ampersand away from its letters. And the favicon turned out to be the old builder's heart logo, still hanging around from the clone.
- **Fixed:** the whole grid re-checked afterward, all 54 rendering on both screens with zero errors. The nav pill's gap set to zero. A new `c&p` favicon on an ink tile, at 64, 180 and `.ico`.
- **Picked:** **x-height**, lowercase `clip&post` set tight as one word, with the ampersand shrunk to lowercase height in rose. "i gave my pick, update, push, make a git for it, lock it in. make the git public"
- **Built after the pick:** the wordmark in the nav and the footer, a first-person README, a build history, AGENTS.md, the MIT license, and the public repo with the live site as its homepage (`255703e`).
- **Tested:** the same live checks at 1440 px and 390 px, all passing again, and the favicons return 200. The full history was searched for names that shouldn't be public: zero hits.
- **Wanted next:** a banner for the repo, and the old .com pointed somewhere alive.

## 5. Feature family tree

```
one card to hide → the site is half dead, no source anywhere
└─ exact mirror → Cloudflare Worker on my own subdomain
   └─ "less vibe coded" → lab round 1: 20 directions
      ├─ Reel Wall: tiles slide in on open
      ├─ Field Tiles: the punchy headline
      └─ Big Numerals: clean
         └─ round 2: 20 refinements → Tilted Plane + Tilted Floor
            └─ round 3 merge → live
               ├─ wrong calendar found → every button on my booking page
               └─ "only thing i dont like is logo" → 54-option logo lab
                  └─ x-height wordmark → c&p favicon replaces the builder's heart
                     └─ public repo
```

## 6. Test log

| When (2026) | What | Result | Where |
|---|---|---|---|
| Nov 2, 17:43 | Clone vs original, full-page screenshots | Identical apart from the removed card and the badge | Private note |
| Nov 2, 17:43 | Live clone | 200, zero matches for the removed card, fallback routing works | Private note |
| Nov 2, about 18:25 | Lab round 1 | 20 of 20 load with zero errors; each checked at desktop and phone width | Private note |
| Nov 2, about 19:00 | Lab round 2 | 20 of 20 load with zero errors | Private note |
| Nov 2, 19:19 | Live redesign, Playwright at 1440 and 390 | 6/6 booking buttons, 19/19 creator links, 11/11 sections, FAQ opens, zero broken images, overflow, console errors or failed requests | Private note |
| Nov 2 | Logo lab | 54 of 54 render on both screens, zero errors | Private note |
| Nov 2, 19:57 | Live re-check after the logo | Same as above, favicons 200 | Private note |
| Nov 5 | Live `index.html` and `kit/content.js` vs `main` | Byte-identical; page, content file, favicon and booking link all 200 | My run, `curl` |

There's no CI. It's static files with nothing to build, so the checks above are the record.

## 7. Roads not taken

- **Fixing it inside the builder.** I wanted the site cloned and out of there, on my own domain.
- **Rebuilding before cloning.** The first commit is the old build, byte for byte, so the live site stayed identical while the redesign happened. The rebuild came after.
- **Cloudflare Pages.** It runs as a Worker with static assets, the same way my other lorecraft.io sites deploy.
- **The builder's badge.** It was the host's overlay, never part of the site.
- **The other 18 round-2 options and 53 logo options.** Hidden from the lab grids, with their files kept.

## 8. What's next

- Point clipandpost.com at the Worker. It still shows the dead builder page.
- A banner for this repo.

## 9. Sources

- Commits: `git log` of `fidgetcoding/clipandpost`.
- [docs/BUILD-HISTORY.md](docs/BUILD-HISTORY.md): my first write-up, from the same day.
- Private, kept by me: three session notes dated November 2, 2026 (the clone and lab round 1, the redesign shipping, the wordmark and the public repo).
