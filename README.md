# Dragster Lab

A single-page physics simulator and legality checker for TSA's **Dragster Design**
event, built around the rule change between the 2027 and 2028 competition years.

**Live tool:** just `index.html` — no build step, no dependencies to install.

## What changed for 2027–2028

The High School Competitive Events Guide for the 2027 & 2028 National TSA
Conferences moves the dragster body in the *opposite* direction from the
2025→2026 change — cars get longer and meaningfully heavier at the floor:

| Spec              | 2027        | 2028        |
|--------------------|-------------|-------------|
| Body length         | 265–275 mm  | 290–300 mm  |
| Body mass (no CO2)  | 60 g min    | 85 g min    |

For context, the 2026 spec (previous conference cycle) capped length at
250–260 mm with a 50 g mass floor — so 2027–2028 reverses that shrink-the-car
trend and pushes cars bigger and heavier instead. Everything else in the
dimensional spec (wheelbase, wheel sizes, axle placement, CO2 chamber, screw
eyes) is unchanged.

Two non-dimensional changes are also worth knowing about:

- **Documentation Portfolio.** The old "one drawing + one materials-list page"
  check-in is replaced by a full portfolio (title page, table of contents,
  technical drawing, materials list, and a required **Resources and AI
  Reflection** form), scored separately as its own 50-point rubric section.
- **GenAI use is now explicitly permitted** for this event — a reversal of
  the outright ban in the 2025–2026 guide. The AI Reflection form asks
  participants to explain how (or whether) they used AI tools and to reason
  about the ethics/effectiveness of that choice.

This tool surfaces the dimensional delta up front, then lets you check a
design and simulate a run under either rule set. It does not implement a
Documentation Portfolio checker — see the official rating form for that
rubric.

## What's inside

- **Rule delta table** — the full dimensional spec, both years, changed rows
  flagged.
- **Legal design checker** — plug in your car's measurements, toggle 2027 or
  2028, get a pass/fail on every dimensional rule.
- **Physics lab** — a launch-impulse model (CO2 thrust pulse → rolling
  resistance + aerodynamic drag → coast to the 20 m finish line), with two
  side-by-side designs (A/B) you can tune independently and compare on
  20 m time, top speed, and total mass. Defaults are pre-loaded as a
  shorter/lighter 2027-spec car (A) vs. a longer/heavier 2028-spec car (B).
- **Track telemetry** — an animated 20 m strip that plays back Design A's
  simulated run with a light-tree launch sequence.

## On the physics model

This is a standard trapezoidal-thrust-impulse model, not an official TSA
tool and not a manufacturer thrust curve for CO2 cartridges. The sliders
(peak thrust, burn duration, rolling resistance μ, drag coefficient, frontal
area) are reasonable starting points, not measured constants. If you have a
stopwatch time from an actual run, tune the sliders until the simulated
finish time matches — after that, the relative comparisons (mass up 15 g,
length down 30 mm, etc.) become meaningful for your specific build.

Always check the current year's **Themes & Problems** page at
[tsaweb.org](https://tsaweb.org/competitions/themes-and-problems) for any
special annual design challenge — this tool covers the dimensional/mass
rules only, not theme-specific requirements.

## Deploying to GitHub Pages

1. Create a new repo (or use an existing one) and add `index.html` and this
   `README.md` to it.
2. Push to GitHub:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Add dragster design lab"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**, set **Source** to `main` branch,
   root folder, and save.
4. Your simulator will be live at
   `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## Sources

- TSA *High School Competitive Events Guide for the 2027 and 2028 National
  TSA Conferences* — Dragster Design event (Rule DB/A/S/P/E/W, Regulations &
  Requirements, Official Rating Form).
- 2026-cycle figures used for historical comparison are from the *2025 and
  2026* edition of the same guide, cross-checked against Virginia TSA and
  Washington TSA affiliate postings.

## License

Do whatever you want with this — it's a study aid, not a product.
