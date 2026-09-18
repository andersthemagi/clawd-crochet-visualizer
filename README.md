# Clawd the Crab, round by round

A 3D walkthrough of the free **Clawd the Crab** amigurumi pattern. Each step
shows one instruction and renders the piece as it should look at that point,
built from the pattern's own stitch counts rather than modelled by hand.

Live: https://clawd.redmage.cc

## Attribution

The pattern is **Clawd the Crab by [Chrisette Designs](https://www.chrisettedesigns.com/patterns/clawd-the-crab-free-crochet-pattern/)**,
published free on their site. It is theirs, not mine. This viewer reproduces the
instructions with credit and links back to the original everywhere it appears,
including six technique videos from Chrisette's own channel.

**Open question before wider promotion:** whether the instruction text may be
reproduced verbatim, or whether this should link out for the wording and show
only the stitch counts. That has not been settled with the designer.

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
