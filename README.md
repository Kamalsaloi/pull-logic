# Pull Logic — hero redesign

A redesign of the [pulllogic.com](https://pulllogic.com) hero section.

Open `index.html` directly in a browser — no build step, no server.

## The two problems this fixes

**1. The live hero auto-rotates two messages every 2 seconds.** You cannot finish
reading the headline, and you cannot click a CTA before it leaves. This version is
static. The NAED announcement isn't deleted — it moves to a persistent, dismissible
ribbon under the nav, where it stays readable and clickable indefinitely.

**2. The live site describes the product in paragraphs.** This version shows the
workflow instead: four signal sources converge into one detected risk, three costed
routes are weighed, one is chosen, and the transfer order is written back to the ERP.

The decision card is the part that matters. It shows the two **rejected** options
with the reason each one lost — *day 7, $4,200, still a day short* and *2 accounts
contract-blocked*. An alerting dashboard can show you a problem. Only a decision
engine can show you the options it ruled out.

## Layout

| Breakpoint | Behaviour |
|---|---|
| 1341px+ | Full size, four stages left to right |
| ≤1340px | Headline 54px, type and padding step down |
| ≤1180px | Headline 48px, tighter connectors and imagery |
| ≤920px | Flow stacks vertically, connectors rotate to point down |
| ≤1080px | Nav collapses to a burger |

Nothing overflows and nothing scrolls horizontally at any width. Verified at 485,
683, 938, 1078, 1238 and 1438px.

## Design system

Dark, but never pure black — the ground is `#0D0D0C`, text is `#EDEDEA`.

| Token | Value | Role |
|---|---|---|
| `--ground` | `#0D0D0C` | Page |
| `--panel` | `#161514` | The workflow surface |
| `--amber` | `#F5A524` | Pull Logic acting. Brand equity, used sparingly |
| `--risk` | `#E3594B` | The detected risk |
| `--signal` | `#7C8B99` | Incoming data only |
| `--ok` | `#3FB27F` | Executed |

Four accents, each semantically earned. Cards use a tinted-glass fill rather than a
solid so they lift off the ground; the panel uses a graded border (bright at the top,
dark at the bottom) so it reads as a surface catching light rather than an outline.

Type is Geist, with IBM Plex Mono reserved strictly for machine data — SKUs, order
IDs, quantities, timestamps. That split is what makes the panel read as a live
system rather than an illustration.

## Accessibility

- Real `<nav>`, `<h1>`, `<main>` and anchors; `aria-current="page"` on the active nav item
- Alt text on every image, `aria-hidden` on decorative SVGs
- All text meets WCAG AA against its background (the quietest, `--dim` on `--panel`, is 4.8:1)
- No text below 11px

## Known gaps

- The burger button is decorative. There is no mobile menu behind it.
- The product shot and transfer scene in `assets/` are AI-generated placeholders.
  Swap them for real photography before this ships.
- Geist is flagged by some design linters as an overused default face. It is used
  here at the client's request.

## explorations/

Earlier directions, kept for reference and not part of the deliverable:

- `hero-webgl.html` — the workflow as a real 3D isometric network (Three.js). Column
  height is days of inventory cover against a translucent target plane, so you can
  see Denver sitting under the line while Kansas City punches through it. The
  strongest artifact of the set, but heavy for a hero.
- `hero-animated.html` — the same decision as an animated inventory curve, showing
  all three candidate routes as paths. Runs once, user-controllable.
- `hero-3d.html` — an SVG isometric precursor to the WebGL version.
- `hero-static.html` — the first static build.
- `concepts/`, `network-map.jpg` — generated imagery explored and set aside.
