# GitHub Profile README Builder Console Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the current generic GitHub profile README with a memorable Builder Console profile anchored around Toolover.

**Architecture:** The implementation is static and GitHub-safe: one repo-hosted SVG banner plus a concise Markdown README. The SVG owns the visual first impression; the README owns accessible text, project context, stack, links, and stats.

**Tech Stack:** GitHub Markdown, inline-safe HTML for image alignment only, SVG, shell validation commands.

---

## File Structure

- Create: `assets/builder-console.svg`
  - Responsible for the dark technical hero banner.
  - Must be self-contained SVG text/shapes, no remote fonts or external images.
- Modify: `README.md`
  - Responsible for the public GitHub profile content.
  - Must reference `assets/builder-console.svg` using a relative path.
- Keep: `old-readme.md`
  - Historical copy. Do not edit.
- Keep ignored: `.superpowers/`
  - Visual companion artifacts. Do not commit.

---

### Task 1: Add Builder Console SVG Banner

**Files:**
- Create: `assets/builder-console.svg`

- [ ] **Step 1: Write the failing validation**

Run:

```bash
test -f assets/builder-console.svg
```

Expected: FAIL because `assets/builder-console.svg` does not exist yet.

- [ ] **Step 2: Create the SVG banner**

Create `assets/builder-console.svg` with this content:

```svg
<svg width="1200" height="420" viewBox="0 0 1200 420" fill="none" xmlns="http://www.w3.org/2000/svg" role="img" aria-labelledby="title desc">
  <title id="title">Derek Nguyen Builder Console</title>
  <desc id="desc">A dark command console banner for Derek Nguyen, software engineer and product builder currently building Toolover.</desc>
  <rect width="1200" height="420" rx="28" fill="#08111F"/>
  <rect x="1" y="1" width="1198" height="418" rx="27" stroke="#1F6FEB" stroke-opacity="0.75" stroke-width="2"/>
  <path d="M0 92H1200" stroke="#1F2937" stroke-width="2"/>
  <circle cx="45" cy="46" r="8" fill="#F87171"/>
  <circle cx="72" cy="46" r="8" fill="#FBBF24"/>
  <circle cx="99" cy="46" r="8" fill="#34D399"/>
  <text x="132" y="52" fill="#7DD3FC" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="18" font-weight="700" letter-spacing="2">TOOLOVER.WORK / BUILDER CONSOLE</text>
  <text x="1004" y="52" fill="#94A3B8" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="16">HCMC · UTC+7</text>
  <text x="56" y="152" fill="#E6EDF3" font-family="Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif" font-size="52" font-weight="800">Derek builds tools that</text>
  <text x="56" y="212" fill="#E6EDF3" font-family="Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif" font-size="52" font-weight="800">remove tiny developer frictions.</text>
  <text x="58" y="262" fill="#A5B4FC" font-family="Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif" font-size="24">Free browser-first utilities, backend systems, and small internet products.</text>
  <rect x="742" y="126" width="402" height="202" rx="18" fill="#0F172A"/>
  <rect x="743" y="127" width="400" height="200" rx="17" stroke="#334155" stroke-width="2"/>
  <text x="772" y="168" fill="#22C55E" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">$ now</text>
  <text x="772" y="198" fill="#CBD5E1" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">building toolover.work</text>
  <text x="772" y="238" fill="#22C55E" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">$ stack</text>
  <text x="772" y="268" fill="#CBD5E1" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">ruby go node react</text>
  <text x="772" y="308" fill="#22C55E" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">$ mode</text>
  <text x="865" y="308" fill="#CBD5E1" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="20">ship small, useful, public</text>
  <rect x="56" y="324" width="78" height="34" rx="9" fill="#1E293B" stroke="#334155"/>
  <text x="82" y="347" fill="#E2E8F0" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="16">JSON</text>
  <rect x="148" y="324" width="78" height="34" rx="9" fill="#1E293B" stroke="#334155"/>
  <text x="178" y="347" fill="#E2E8F0" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="16">Code</text>
  <rect x="240" y="324" width="66" height="34" rx="9" fill="#1E293B" stroke="#334155"/>
  <text x="263" y="347" fill="#E2E8F0" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="16">API</text>
  <rect x="320" y="324" width="120" height="34" rx="9" fill="#1E293B" stroke="#334155"/>
  <text x="346" y="347" fill="#E2E8F0" font-family="ui-monospace, SFMono-Regular, Menlo, Consolas, monospace" font-size="16">Text tools</text>
</svg>
```

- [ ] **Step 3: Run SVG validation**

Run:

```bash
test -f assets/builder-console.svg
rg -n "Derek builds tools|toolover.work|ship small" assets/builder-console.svg
```

Expected: PASS. `rg` prints lines containing the headline, Toolover anchor, and mode text.

---

### Task 2: Replace README Content

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Write the failing validation**

Run:

```bash
rg -n "assets/builder-console.svg|Toolover|Developer friction" README.md
```

Expected: FAIL or incomplete because the current README still references the old greeting, old stats placement, and Muerta Toolbox copy.

- [ ] **Step 2: Replace README with Builder Console copy**

Replace the entire `README.md` with:

```markdown
<p align="center">
  <img src="./assets/builder-console.svg" alt="Derek Nguyen builds tools that remove tiny developer frictions" width="100%" />
</p>

## Hey, I'm Derek Nguyen

I'm a software engineer in Ho Chi Minh City building practical developer utilities, backend systems, and small internet products. I like tools that are fast to open, useful without ceremony, and calm enough to become part of a daily workflow.

### Now building

[**Toolover**](https://toolover.work) is my current product focus: a suite of free browser-first developer tools for JSON, code formatting, API helpers, text utilities, and everyday workflow cleanup.

I'm also exploring other small developer-product experiments around useful, public, no-login software.

### Builder stack

| Area | Tools |
| --- | --- |
| Backend | Ruby, Go, Node.js |
| Frontend | React, JavaScript, HTML, CSS |
| Data | PostgreSQL, MySQL, Redis |
| Cloud | AWS, Google Cloud, DigitalOcean |
| Product mode | Ship small, useful, public |

### Around the web

- Building: [toolover.work](https://toolover.work)
- Writing: [dereknguyen.substack.com](https://dereknguyen.substack.com)
- Social: [x.com/dereknguyen269](https://x.com/dereknguyen269)
- GitHub: [@dereknguyen269](https://github.com/dereknguyen269)

### GitHub signal

<p>
  <img src="https://github-readme-stats.vercel.app/api?username=dereknguyen269&show_icons=true&hide_border=true&theme=github_dark" alt="Derek Nguyen GitHub stats" />
</p>

---

I like coffee, developer tools, and the kind of engineering work that quietly saves people time.
```

- [ ] **Step 3: Run README validation**

Run:

```bash
rg -n "builder-console.svg|Toolover|toolover.work|Muerta|Giphy|media.giphy.com" README.md
```

Expected: PASS for `builder-console.svg`, `Toolover`, and `toolover.work`; no `Muerta`, `Giphy`, or `media.giphy.com` lines should appear.

---

### Task 3: Final Verification And Commit

**Files:**
- Verify: `README.md`
- Verify: `assets/builder-console.svg`
- Verify ignored: `.superpowers/`

- [ ] **Step 1: Check final git status**

Run:

```bash
git status --short
```

Expected: only `README.md` and `assets/builder-console.svg` are unstaged, unless the implementation plan is being committed separately.

- [ ] **Step 2: Check SVG path and old artifacts**

Run:

```bash
test -f assets/builder-console.svg
rg -n "assets/builder-console.svg" README.md
rg -n "Muerta|media.giphy.com|VgCDAzcKvsR6OM0uWg|LnQjpWaON8nhr21vNW" README.md
```

Expected: first two commands PASS. Final `rg` command FAILS with no matches.

- [ ] **Step 3: Review diff**

Run:

```bash
git diff -- README.md assets/builder-console.svg
```

Expected: README is replaced with Builder Console structure; SVG banner is new; `.superpowers/` does not appear.

- [ ] **Step 4: Commit**

Run:

```bash
git add README.md assets/builder-console.svg
git commit -m "Redesign GitHub profile README"
```

Expected: commit succeeds.
