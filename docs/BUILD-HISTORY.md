# How clip&post came together

Live: **[clipandpost.lorecraft.io](https://clipandpost.lorecraft.io)**

This all happened in one day, November 2, 2026, with a lot of design labs.

## 1. The rescue

It started small. I wanted one client card, GLITCH, off the site for a while. When I went looking, it turned out the site wasn't where I thought it was. clipandpost.com pointed at a builder I'd stopped paying for, so it was showing a "this app isn't available yet" page. The only working copy was an old build on a hosted builder subdomain, and there was no source repo anywhere.

So I cloned it: every file of the built site (HTML, JS, CSS, all 19 avatars) mirrored as-is. Then I made three edits:

- removed the GLITCH card, including its entry, its image and the image file
- stripped the hosting platform's analytics scripts, which would break off their servers
- stripped the "Edit with…" badge

It went up on Cloudflare at `clipandpost.lorecraft.io`. I checked it side by side against the original, and the only differences were the card and the badge. The lorecraft.io case study now links here.

Commits: `be1d7b6` (the untouched mirror), `666f133` (the edits plus the Worker config).

## 2. Design lab, round 1: 20 directions

The clone worked, but it still looked like a template: centred everything, purple pills, identical cards. My brief was "much sexier and less vibe coded", still one page, with the same sections and functions.

I built a content kit from the live site's real copy, real creators and real links, then 20 options in 5 families:

| Family | Options |
|---|---|
| Editorial | Cover Story, Broadsheet, The Spread, Contents Page |
| Numbers | Scoreboard, Quote Board, Big Numerals, Broadcast |
| Feed | Reel Wall, Edit Timeline, Swipe Feed, Burned-in Captions |
| Poster | Swiss Red, Headliner, Field Tiles, Cut & Tape |
| Studio | Salon, Ledger, Orbit, Monograph |

Every option was screenshot-checked at desktop and phone width: all 11 sections present, working FAQ, no sideways scroll.

My picks:
- **Reel Wall**: "the sliding tiles right on opening is great"
- **Field Tiles**: "i love how punchy the lets go viral at the top is"
- **Big Numerals**: "i love how clean this one is"

## 3. Round 2: 20 refinements

The rules for this round came from those picks: motion on open, an oversized punchy headline, and a clean structure below the fold. The families:

- **Reel Wall+** (4), which pushes how the wall moves
- **Punch+** (4), which keeps the headline and calms the rest
- **Clean+** (4), which sharpens the numerals look
- **Hybrids** (8), which mix all three in different amounts

Partway through I hit my usage limit, switched accounts and restarted the batch.

My two favourites both came from one idea, a tilted 3D tile wall: **Tilted Plane** (Reel Wall+) and **Tilted Floor** (Hybrids).

## 4. Round 3: the merge

I liked Tilted Plane from the opening through Our Proven Strategy, and Tilted Floor for everything after. The merge kept each half's layout and moved the bottom onto the top half's palette and type: rose `#e5195e`, warm white, Big Shoulders, Hanken Grotesk and IBM Plex Mono. A pair of crossing scroll ribbons stitches the two halves together.

I also fixed the calendar. Every button now goes to my Morgen booking page, where the old site pointed to the wrong one.

Shipped in `65f4978`. Live checks at 1440px and 390px:

- all 6 booking buttons go to Morgen in a new tab
- all 19 creator links work
- all 11 sections are present and the FAQ opens
- no broken images, no overflow, no console errors

## 5. The logo

The site was locked, but the logo wasn't: it was a pill with `clip [+] post`. The lab for it had 54 options: 9 ideas × 6 versions.

- Ampersand
- Cut
- Monogram
- Stacked
- 9:16 Frame
- Play glyph
- Display type
- Tilted
- Tape

Each option was shown large and in the real nav.

My pick was **x-height**: lowercase `clip&post` set tight as one word, with the ampersand shrunk to lowercase height in rose. That replaced the nav and footer logo. A matching `c&p` favicon replaced the old builder's heart icon, which had been hanging around since the clone.
