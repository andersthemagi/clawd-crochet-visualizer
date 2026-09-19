# Crochet your own Clawd

A 3D walkthrough of the free **Clawd the Crab** amigurumi pattern. Each step
shows one instruction and renders the piece as it should look at that point,
built from the pattern's own stitch counts rather than modelled by hand.

Made for [Claude Community House](https://claudebcn.com), a free community-run
week of Claude workshops in Barcelona, 21 to 24 September 2026. That event is
run by the European Claude ambassadors and is not an official Anthropic event.

Live: https://clawd.redmage.cc

## Attribution

The pattern is **Clawd the Crab by [Chrisette Designs](https://www.chrisettedesigns.com/patterns/clawd-the-crab-free-crochet-pattern/)**,
published free on their site. It is theirs, not mine. This viewer reproduces the
instructions with credit and links back to the original everywhere it appears,
including six technique videos from Chrisette's own channel.

Her stated terms on the pattern page, quoted in full:

> This is a Chrisette Designs original design. This pattern is NOT to be SOLD.
> You may sell what you make, but must use your own photos and should credit me
> by showing the link to my pattern here.

This tool is free, uses its own photography, credits her and links to the
pattern from every screen. She asks for Ko-Fi support on the same page, so the
viewer links that too.

This viewer was built by Andrés at [Red Mage](https://contra.com/andersthemagi).

## How it works

Stitches are nodes in a graph. Each one records the specific parent loop it is
worked into, so an increase puts two stitches into one parent and a decrease
anchors to two. The shape comes from relaxing that graph: springs to the parent
and to the neighbour in the round, stuffing pressure along each stitch's surface
normal, bending resistance across rounds, and short-range repulsion for yarn
thickness. Nothing about the finished shape is drawn by hand.

Stitch geometry is a per-type unit cell informed by published work: Storck et
al. 2022 for the depth ratio and the yarn-diameter limit, ball-band gauge data
for the square aspect of a single crochet, and the CT2Yarn micro-CT centrelines
(`ct2yarn_stitch_templates.json`, MIT) as a proportion cross-check.

A validation check worth knowing about: real amigurumi goes visibly hexagonal
when increases are stacked instead of staggered. This pattern stacks them, and
the solver reproduces six corners without being told to. Run
`window.__dbg.hexTest(round)` in the console.

## Running it

It is one static file with no build step. Any static server works:

```bash
python3 -m http.server 4173
```

## Console helpers

- `window.__dbg.view(azimuth, elevation)` moves the camera. 0 azimuth is the front.
- `window.__dbg.get()` reports per-round stitch count, radius and height.
- `window.__dbg.hexTest(round)` counts radius peaks around a round.
- `window.__dbg.claw()`, `window.__dbg.eyes()` for the attached pieces.
