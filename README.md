# Iminda & Ahinsa — Homecoming Invitation

The second-day (homecoming) invitation for the same couple as the first-day
wedding invitation. Single-page, static HTML/CSS/JS. No build step, nothing to
`npm install`. Tailwind and the web fonts load from CDNs, so the page needs a
network connection.

## The details

| | |
|---|---|
| Couple | Iminda (son of Mr. & Mrs. Liyanage) and Ahinsa (daughter of Mr. & Mrs. Vithanage) |
| Occasion | Homecoming |
| Date | Wednesday, 18 November 2026 |
| Time | 5.30 pm to 10.30 pm |
| Venue | Summerfields, Kottawa — No. 139 Piliyandala Road, Palanwatta, Pannipitiya |
| RSVP | Malani 072 146 0888, Iminda 071 610 8116 |

Note the name order is reversed from the first-day invitation. The printed
homecoming card reads "Iminda & Ahinsa", with the groom's lineage first, and
this page follows the card.

## View it locally

Open `index.html` in a browser, or drag it into a window.

## Colour

Wine red and black, per the client's request. The tokens are in the
`tailwind.config` block at the top of `index.html`:

| Token | Hex | Use for |
|---|---|---|
| `ink` / `ink-2` / `ink-3` | `#120909` / `#1B0F0E` / `#241413` | Grounds, all red-tinted near-blacks |
| `wine` | `#9C2A26` | Button fills and large blocks, never small text |
| `wine-bright` | `#E08279` | Small caps labels and accents |
| `wine-deep` | `#6B1714` | Hover states |
| `cream` | `#F4ECE7` | Primary text |
| `muted` | `#C8B4AE` | Secondary text |

Every hue sits at 0 to 5 degrees, i.e. true red. An earlier version sat at
345 to 353 degrees and read visibly purple. The giveaway is the blue channel:
when blue exceeds green the colour swings towards magenta however dark it is.
Keep blue at or below green in any replacement.

`wine-bright` is light rather than a deep red for a measured reason. The
page has a wine glow (`#page-glow`) at 42% opacity lifting the background behind
the hero labels and the card headers. At a deeper accent, 12px uppercase labels
landed at 4.05:1 on the bare glow and 3.69:1 where the glow sits under a panel,
both short of the 4.5:1 needed for small text. Lightening the accent fixes both
at full glow strength, so the glow did not have to be dimmed. Re-check with a
contrast script if you change either the accent or the glow opacity.

The placeholder colour is set explicitly rather than as a transparent `muted`,
because `muted` at 60% computed to 3.71:1.

## Motion

- **The hero entrance waits for the cover.** The lineage lines, names and
  ampersand rise in only once the guest taps to open. They are held with
  `animation-play-state: paused` until `body` gains the `entered` class;
  otherwise the entrance plays unseen behind the overlay.
- **Sections reveal on scroll.** Add `reveal` to any block; `--reveal-delay`
  staggers siblings. Reveals fire once, so scrolling back never re-hides them.
- **Reduced motion is respected** throughout.

Note that scroll reveals cannot be verified with `chrome --headless --dump-dom`.
That mode never paints, so IntersectionObserver callbacks never fire and
everything looks stuck at zero opacity. Drive a real browser instead.

## Typography

Names are Pinyon Script, whose capital A is unambiguous. Great Vibes is loaded
only for the ampersand, where its flourish is far better than Pinyon's small
mark, and where the shape is decorative rather than a letter to be read.
Headings are Playfair Display, body text Inter, and the lineage and pull quotes
Cormorant Garamond italic.

## Features

- Touch-to-open cover
- Live countdown to 5.30 pm on 18 November 2026
- Add to Calendar (.ics download, 5.30 pm to 10.30 pm Sri Lanka time)
- Get Directions, opening the venue address in Google Maps
- RSVP form that hands off to WhatsApp, pre-filled, addressed to whichever of
  the two contacts the guest picks
- Tap-to-call and copy-number for both contacts
- Botanical corner motif drawn as inline SVG, no image files

## Deploying free (GitHub Pages)

Push this folder to a GitHub repository, then **Settings → Pages → Source** and
pick the `main` branch with `/ (root)`. It publishes at
`https://<username>.github.io/<repo>/` within a minute or two.
