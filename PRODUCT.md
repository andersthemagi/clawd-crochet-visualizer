# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Beginner and improving crocheters working through the free "Clawd the Crab"
pattern, with a hook in one hand and yarn in the other. They are mid-project,
looking up between rounds, reading one instruction, then looking back down at
their hands. The tool competes with a printed pattern page and a phone propped
against a mug.

A second audience evaluates the practice rather than uses it: people deciding
whether to hire Red Mage. They are real but secondary. Where the two conflict,
the crocheter wins.

## Product Purpose

Show what a written crochet round actually produces, in 3D, one step at a time.
A written pattern asks a beginner to hold a shape in their head that they have
never seen; the common failure is working three rounds past a mistake before
noticing. Success is a crocheter finishing Clawd who would otherwise have
stalled, and knowing at every step both what to do and what it should look like.

## Positioning

No commercial crochet tool renders a 3D preview. Charting tools (Stitch Fiddle,
Crochet Charts) are 2D symbol editors. The only 3D work that exists is research
code and two hobby projects. The mechanism here is a stitch graph solved with
physical relaxation: stitches are nodes, each anchored to the specific parent
loop it is worked into, with springs to that parent and to the neighbour in the
round, plus outward pressure standing in for stuffing. The shape is derived from
the pattern, not drawn by hand, so the render is an assertion about what the
instructions produce rather than an illustration of it.

## Operating Context

- Built for a crochet session at Claude Community House (https://claudebcn.com),
  Barcelona, 21 to 24 September 2026: a free, community-run week of Claude
  workshops hosted by the European Claude ambassadors. It is **not** an official
  Anthropic event, though Anthropic staff attend, so nothing in the product may
  imply Anthropic endorsement. Andrés is a volunteer there, not a booked speaker.

- Used alongside physical work, not instead of it. Hands are occupied; glances
  are short; the screen may be at arm's length on a table or propped phone.
- The pattern is worked in continuous rounds with a stitch marker, so "which
  round am I on" is a question the user genuinely loses track of.
- Techniques (magic ring, invisible decrease, front loop only) are looked up
  once, on first encounter, then never again.
- Off-screen state matters: stuffing the piece, inserting safety eyes, and
  sewing on claws happen at specific points and cannot be undone easily.

## Capabilities and Constraints

- Three sections, each walked through round by round and ending in its own
  finishing step: Body, Belly, Claws.
- The pattern is expressed as ops strings (`(sc, inc) x6`) parsed into a stitch
  graph. Supported stitches: sc, inc, dec, ch, sl st, front/back loop only.
- The 3D view is WebGL via three.js from a CDN. Currently one self-contained
  HTML file with no build step. This is the present implementation, not a
  commitment: the user explicitly declined to make it binding.
- The belly is optional in the source pattern: skipping it makes Clawd a flat
  applique for a pin or patch. The viewer says so on the belly's first step.
- Finished size per the pattern: about 6.0 cm wide by 5.7 cm long.

## Brand Commitments

- Ships on the redmage.cc domain. It must not read as the Red Mage brand, and
  must be safe to sit beside it.
- The current visual world is dark, spartan, sans-serif, with a single amber
  accent (#ffc23d) reserved for the current round, the primary action, and the
  current step. Orange yarn, deliberately not the red of the original photos,
  and deliberately not Red Mage red.

## Evidence on Hand

- The pattern belongs to Chrisette Designs (Lizette):
  https://www.chrisettedesigns.com/patterns/clawd-the-crab-free-crochet-pattern/
  Her stated terms, verified on the page 2026-09-19: "This pattern is NOT to be
  SOLD. You may sell what you make, but must use your own photos and should
  credit me by showing the link to my pattern here." This tool is free, uses its
  own photography, credits her and links back throughout, so it sits inside
  those terms. Settled, not open. Her photographs are a separate matter and are
  not used. Contact: chrisettedesigns@yahoo.com, Ko-Fi at
  https://ko-fi.com/chrisettedesigns.
- Eleven technique resources (video plus article each), every URL verified
  2026-09-18. Six of the videos are Chrisette's own, embedded in the pattern.
- The pattern page intermittently returns a WordPress database error, so any
  deep link needs a fallback.
- No user testing has happened. No usage data exists. Nothing about adoption,
  completion rates, or crocheter feedback may be claimed.

## Product Principles

1. One step on screen at a time. The user is mid-task with busy hands; anything
   that is not this round is noise.
2. The render is a claim about the pattern. When the model and the photographs
   disagree, the model is wrong and gets fixed, rather than the photo being
   treated as a stylistic variant.
3. Never leave the user guessing where they are or what comes next. Position and
   the next action are always visible without a click.
4. Techniques surface on first encounter and then get out of the way.
5. Credit the designer everywhere the pattern appears.

## Accessibility & Inclusion

Accessibility-first, matching the practice's own positioning. Keyboard operable
throughout, contrast-compliant text, visible focus, and touch targets sized for
someone tapping with yarn in hand. A user who cannot get the WebGL view, or
cannot use it, must still be able to work the whole pattern from the panel.
