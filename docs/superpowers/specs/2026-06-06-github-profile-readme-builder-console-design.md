# GitHub Profile README Redesign: Builder Console

## Goal

Redesign Derek Nguyen's GitHub profile README so it feels memorable, technical, and product-led instead of a generic profile template.

The README should position Derek as a software engineer and product builder currently building Toolover, with room for other small developer-product experiments.

## Current Surface

The existing README is friendly but conventional:

- Greeting-led headline.
- Several personal bullets.
- GitHub stats floated to the right.
- A Ruby-style constant block listing skills.
- Giphy/emoji personality touches.

The redesign should keep the friendliness but replace the template feel with a stronger first impression.

## Visual Direction

Use the **Builder Console** direction.

The README should feel like a compact command center:

- Dark technical banner as the first viewport signal.
- Monospace console labels for current work and stack.
- A short product-builder headline.
- Toolover as the primary current project.
- Crisp sections below the banner, not a long decorative landing page.

The visual device is a repo-hosted SVG banner that GitHub can render reliably. The banner should avoid generic purple gradients, decorative blobs, emoji icons, and invented metrics.

## Content Structure

1. **Hero Banner**
   - Repo-hosted SVG image.
   - Headline: "Derek builds tools that remove tiny developer frictions."
   - Console details:
     - `now`: building `toolover.work`
     - `stack`: Ruby, Go, Node.js, React
     - `mode`: ship small, useful, public
   - HCMC / UTC+7 location cue.

2. **Short Intro**
   - One paragraph that states Derek is a software engineer in Ho Chi Minh City building developer utilities, backend systems, and small internet products.

3. **Now Building**
   - Toolover as the anchor project.
   - Describe it as a suite of free browser-first developer tools for JSON, code, API, text, and practical workflow utilities.
   - Mention other experiments without inventing names: "other small developer-product experiments."

4. **Builder Stack**
   - Compact stack grouped by purpose:
     - Backend: Ruby, Go, Node.js
     - Frontend: React, JavaScript, HTML, CSS
     - Data: PostgreSQL, MySQL, Redis
     - Cloud: AWS, Google Cloud, DigitalOcean

5. **Connect**
   - Keep GitHub profile links light.
   - Include Toolover and existing social/profile links when available.
   - Keep the tone open and human.

6. **Stats**
   - Keep GitHub stats, but make it secondary.
   - Avoid letting badges dominate the top of the README.

## Copy Tone

The copy should be concise, specific, and practical:

- Product-builder, not resume-only.
- Technical, not cold.
- Confident, not inflated.
- No unverifiable claims or growth metrics.
- Minimal emoji; do not rely on emoji as visual design.

## Implementation Notes

- Create a new SVG banner under `assets/` or another simple repo-local path.
- Replace the existing README with GitHub-safe Markdown and simple HTML where alignment is useful.
- Keep existing `old-readme.md` untouched.
- Do not commit `.superpowers/` visual companion files.
- Preserve existing skill/technology image assets unless the final README no longer uses them.

## Verification

Before calling the redesign complete:

- Render or preview the README locally enough to catch broken image paths and obvious Markdown issues.
- Confirm the SVG banner is referenced with a repo-relative path that GitHub can render.
- Check `git diff` for accidental `.superpowers/` files.
- Read the README once as a first-time visitor and confirm the top section answers:
  - Who is Derek?
  - What is he building now?
  - Why should a developer click through?
