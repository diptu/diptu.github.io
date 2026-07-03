# Homepage TODO

Improvement list from a review of the homepage (`content/_index.md`, `hugo.toml`,
`layouts/index.html`). All 6 priorities are now implemented (2026-07-03).

## Follow-up: research-focus + professional polish pass (2026-07-03)

Beyond the 6 priorities above, did a deeper rewrite specifically to (a) sharpen
the "theoretical KV cache compression" positioning and (b) raise the tone to
match a serious research profile rather than a personal-blog-style page.
Content facts are unchanged; this was framing, structure, and tone only.

- **Cut remaining redundancy.** Research Summary's bullets, the old "Focus
  areas" tag line, and Current Research's bullets were restating the same
  4–5 ideas three times over. Dropped the "Focus areas" line entirely (it
  added no new information over the bullets already there).
- **Added actual research specificity.** Replaced the vague, list-of-topics
  framing in "Current Research" with 3 concrete open questions (KV cache
  information-theoretic lower bounds vs. H2O/SnapKV/KIVI, provable-guarantee
  compression vs. empirical heuristics, compression/long-context tradeoffs).
  These are phrased as questions being explored, not solved results — I
  synthesized them from the reading list and math prep already on the page,
  I didn't invent new claims of achieved work. This is the single highest-value
  change for the "optimize for theoretical KV cache compression" ask: sharp
  open questions read as far more credible to a research-minded reader than
  five restatements of "I'm interested in X."
- **Folded "Research Philosophy" into Current Research** as a framing
  sentence instead of a standalone section — it was itself a restatement of
  the same thesis a 4th/5th time; the underlying idea survives, just not as
  its own heading anymore.
- **Removed the "Status" section** (the 🟢🟡🔵🔴 GRE/IELTS/prep tracker). This
  is the one call most worth flagging: it's genuinely useful info to you, but
  a public research profile showing test-prep progress reads as unfinished
  rather than "best foot forward," and it didn't serve the KV-cache-research
  narrative at all. The one fact worth keeping (that you're actively
  preparing PhD applications) is now a single sentence at the end of Research
  Summary instead. Easy to restore as a section if you'd rather keep it
  visible.
- **Removed all heading emoji** (🧠📚🔬🎓💼🛠📖📍, plus the two inline ones in
  Education). This is the other call most worth flagging: it's a real shift
  in register, from "personal/approachable" to "austere academic" — closer
  to the original nahianahmed.com reference this whole redesign started
  from, and closer to how theoretical CS/ML researchers' pages typically
  look. If you want some personality back, this is a quick revert (just the
  emoji, not the content).
- **Trimmed Professional Experience for focus.** Split into full-detail
  entries for the three ML/research-relevant roles (Freelance ML & Systems
  Engineer, Lab Instructor, Junior Data Scientist) and a condensed
  "Other Professional Experience" list (Product Analyst, Technical Analyst,
  Intern) for the three roles unrelated to ML/research. Nothing was deleted —
  the unrelated history is still there, just not given equal visual weight,
  so the page doesn't make a reader wade through unrelated business-analyst
  bullets to find the research-relevant parts.
- **Reordered Technical Skills** to lead with Machine Learning (PyTorch,
  TensorFlow, scikit-learn) before Programming/MLOps, and demoted Data &
  Analytics + Tools (BigQuery, Tableau, Looker Studio, PHP, etc. — real
  skills, just not research-relevant) using the same appendix styling as
  "Preparation."
- **Added canonical references** for the 3 math-prep topics that had none
  (Numerical Linear Algebra → Trefethen & Bau, Information Theory → Cover &
  Thomas, Optimization Theory → Boyd & Vandenberghe) — these are the
  near-universal standard texts in each area, matching the pattern already
  set by the 2 topics that did cite an author (Strang, Freedman), not
  invented specifics.
- **Fixed a typo in the hero subtitle** (`hugo.toml`): missing space and a
  duplicated "Theoretical" — "Theoretical Machine Learning | Efficient
  Transformers |Theoretical KV Cache Compression" →
  "Theoretical Machine Learning · Efficient Transformers · KV Cache
  Compression."
- **Sharpened the closing CTA** to name the specific research area instead
  of a generic "let's collaborate" line.
- Net effect: 7 `##` sections (was 9), page ~27% shorter, same facts, zero
  fabricated claims — verified via build + screenshots in light and dark.

## Priority 1 — Fix cross-page inconsistencies ✅ Done (2026-07-03)

- [x] Reconcile `content/resume.md` (`/resume/`). Turned out `data/resume.tex`
      (the actual downloadable PDF source) was already accurate and consistent
      with the homepage — `content/resume.md` was the stale one. Rewrote it to
      mirror `resume.tex`'s facts instead of the other way around:
  - [x] Research focus tags updated to match homepage (Efficient LLMs,
        Transformer Theory, KV Cache Compression, etc.)
  - [x] Education dates aligned: Jan 2015 – Dec 2018, CGPA 3.62/4.0
  - [x] Project name aligned: CarbonIQ (was "Carboniq" / "EcoLens" /
        "tinyvibe-anomaly-engine")
  - [x] Experience section now mirrors `resume.tex` exactly (Lab Instructor,
        Product Analyst @ Power Ledger, Jr. Data Scientist @ Me-Solshare).
        Note: the homepage's longer Professional Experience list (InsideMaps,
        Grameenphone, Freelance ML & Systems Engineer as its own entry) isn't
        fully mirrored here — treated as deliberate curation on the 1-page
        PDF/resume rather than an error, so left as-is. Flag if that's wrong.
  - [x] Regenerated `resume.pdf` from `resume.tex` (`pdflatex`) and synced it to
        `static/resume.pdf`, the copy actually served at `/resume.pdf` — it was
        stale/out of sync with `data/resume.pdf` before this
  - [x] Added a Publications section to `resume.md` (title, authors, venue, DOI
        links) reusing the existing `.pub-*` CSS classes, so publication data
        isn't lost now that the standalone page is gone
- [x] Retired `content/publications.md` (`/publications/`) — deleted. Content
      now lives on the homepage and in the new Publications section on
      `/resume/`. No other file referenced `/publications/` (checked).

  Follow-up spotted while verifying: the project has a `public/` directory
  checked into the repo root from a prior full `hugo` build. Hugo's dev server
  serves pages from disk here, so it kept serving a stale cached
  `public/publications/index.html` after the source file was deleted until the
  server was restarted. Not a content bug, but worth deleting `public/` (or
  running a clean `hugo` build) before any deploy so old routes don't linger.

## Priority 2 — Missing essentials for a PhD-applicant profile ✅ Done (2026-07-03)

- [x] Added an email/mailto contact icon (`mailto:diptunazmulalam@gmail.com`) to
      `params.socialIcons` in `hugo.toml` — appears in the icon row at the bottom
      of the homepage
- [x] Linked all three publication titles out to their DOIs, on both the
      homepage (`content/_index.md`) and the resume (`content/resume.md`):
  - [x] "End-to-End OCR Using Synthetic Dataset Generation..." → DOI
        10.1007/978-981-15-3607-6_41
  - [x] "Population Estimation of Rohingya Refugees..." → DOI
        10.1142/S2196888819500246
  - [x] "Early Detection of Glaucoma Using Fuzzy Logic in Bangladesh Context" →
        DOI 10.1109/IS.2018.8710490. User supplied the Scholar citation
        (authors/venue/pages); DOI itself was found via web search and
        cross-checked against a co-author's own publication list before
        adding, since it wasn't on file anywhere in the project. Also added as
        a 3rd Publications entry to `content/resume.md` and `data/resume.tex`
        (it was previously missing from both, not just unlinked) — required
        re-tightening `resume.tex` margins slightly to keep the PDF at 1 page
        after adding the entry, then recompiled `resume.pdf` and synced it to
        `static/resume.pdf`
- [x] Added Google Scholar as a social icon — user confirmed profile URL
      (`scholar.google.com/citations?user=4e8-JGgAAAAJ`)
- [x] Added ORCID as a social icon — user supplied
      `https://orcid.org/0009-0003-5322-5975`
- [x] Kept Facebook icon — user explicitly chose to keep it alongside the new
      icons rather than remove it
- [x] Added a closing CTA above the icon row (`layouts/index.html`): a short
      line ("Interested in collaborating or discussing PhD opportunities?...")
      plus a Resume download button, so the page doesn't run out without a
      second call-to-action
- [x] Follow-up refinement (user request, same theme): removed the Resume
      button from the top hero since it's now redundant with the one in the
      closing CTA — it appears once, at the bottom, alongside the icon row

## Priority 3 — Narrative structure ✅ Done (2026-07-03)

- [x] Trimmed the repeated research pitch from 5 restatements down to 1. What
      changed in `content/_index.md`:
  - "Research Interests" (was its own `##` section) is now a single
        "**Focus areas:** ..." line folded into Research Summary
  - "Current Goal" (was its own `##` section) is now folded into Research
        Summary's opening sentence ("...with the long-term goal of a PhD
        focused on efficient transformer inference and KV cache compression")
  - "Guiding Principle" was kept as-is (it's a distinct methodology quote,
        not a restatement of the pitch) — repositioned near the end; final
        call on whether it belongs at all is still Priority 4's to make
- [x] Reordered sections to front-load research signal, following the order
      suggested in this TODO: Research Summary → Publications → Current
      Research → Education → Professional Experience → Technical Skills →
      Preparation (appendix) → Guiding Principle → Status
- [x] Merged "Research Experience" (Independent Research) and "Research
      Projects" (Mathematical Foundations of Efficient Transformers...) into
      one "🔬 Current Research" section — they described the same ongoing work
      twice with overlapping bullets; combined into a single deduped list
- [x] Bonus merge in the same spirit: "Research Reading" and "Mathematical
      Preparation" combined into one "📖 Preparation" section (two subheadings:
      Papers / Mathematical foundations) since both are appendix-style prep
      material, not core signal — matches the TODO's "Reading List / Math Prep
      (appendix)" grouping
  - Net effect: 13 `##` sections → 9. Content itself is unchanged (nothing
      deleted, only merged/relocated) — verified by screenshot, no console
      errors

## Priority 4 — Tone/formality pass ✅ Done (2026-07-03)

- [x] Decided to keep the quote rather than cut it — it signals focused
      research taste, which reads well to a PhD evaluator — but reworked it to
      fit the formal register instead of standing out as a motivational-poster
      moment next to Education/Publications:
  - Retitled "🧭 Guiding Principle" → "🧭 Research Philosophy" (academic
        framing instead of motivational framing)
  - Dropped the quotation marks and capital "Every" → lowercase "how" — reads
        as a stated principle now, not something quoted from elsewhere
  - Kept the blockquote treatment (pull-quote styling is normal in academic
        personal statements too)
- [x] Added a one-line legend under "📍 Status" rather than relabeling each
      item: *🟢 In progress · 🟡 Starting soon · 🔵 Ongoing · 🔴 Not yet
      started*. Chose a legend over rewriting each entry as plain text because
      I don't actually know which exact stage each item is in (e.g. whether
      IELTS prep is "not started" vs "scheduled") — a legend explains the
      existing colors without me guessing at facts about your life. If the
      legend still feels off, the fix is either to correct my guessed
      color-to-meaning mapping or swap to plain-text status per item — just
      say which.

## Priority 5 — Content cleanliness ✅ Done (2026-07-03)

- [x] Fixed the stray double blank line under "Technical Skills → Machine
      Learning" in `content/_index.md` (was two blank lines before "### MLOps
      & Systems", now one)
- [x] Made the Education block spacing consistent — removed the blank line
      that split CGPA into its own paragraph; University / Degree / Dates /
      CGPA now render as one continuous hard-break block, matching how every
      other entry (Experience, etc.) is formatted
- [x] Updated site-wide `description` in `hugo.toml`: "A personal blog about
      Machine Learning and Software Engineering" → "Nazmul Alam Diptu —
      working on efficient transformer inference and KV cache compression,
      transitioning into a PhD in theoretical machine learning." Verified in
      the built `<meta name=description>` tag
- [x] Decided on the browser tab title / branding question: changed
      `title` in `hugo.toml` from `'~ ❯ diptu'` → `'Nazmul Alam Diptu'`.
      Reasoning: every other decision this session has pushed toward a
      formal academic identity (Scholar/ORCID icons, "Research Philosophy"
      retitle, PhD-focused homepage copy) — a terminal-handle browser tab
      title cuts against that, and it's what shows in Google results and the
      tab bar if a PhD reviewer looks the name up. This also changes the nav
      logo text and footer copyright line, since both read from `site.Title`
      — checked via screenshot, fits fine, no layout issues. If the terminal
      branding was intentional personality you want kept, this is a one-line
      revert in `hugo.toml`.

## Priority 6 — UX/structure polish ✅ Done (2026-07-03)

- [x] Added a sticky jump-to-section nav. Implementation:
  - `hugo.toml`: added `[markup.tableOfContents]` with `startLevel`/`endLevel`
        = 2, so Hugo's auto-generated `.TableOfContents` only picks up the 9
        `##` sections, not the `###` job-title sub-headings
  - `layouts/index.html`: renders `.TableOfContents` in a `<nav class="home-toc">`
        right below the hero, before the content
  - `assets/css/extended/custom.css`: styled it as a horizontal, wrapping pill
        row (`position: sticky; top: var(--header-height)`), so it stays
        visible while scrolling and reuses the theme's own header-height
        variable rather than a hardcoded offset
  - Verified: all 9 sections present with matching anchors, sticky behavior
        holds on scroll, clicking a pill jumps to the right section, works in
        both light and dark
- [x] Added visual hierarchy for the two appendix-style spots the TODO named
      (Reading List + Math Prep, now merged into "Preparation"; and "Tools"
      under Technical Skills): wrapped their content in
      `<div class="appendix-section">` / `<div class="appendix-inline">` in
      `content/_index.md` and styled both with smaller, secondary-colored
      text in `custom.css`. Headings were left outside the wrapper (still
      full-size, still show up correctly in the TOC) — only the body content
      recedes. Publications/Research Summary/Current Research etc. are
      untouched, so they read as the default (higher-emphasis) tier by
      contrast.
- [x] Added `aria-hidden="true"` spans around every heading emoji (all 9 `##`
      sections) plus the two inline emoji in the Education section (🎓 Merit
      Scholarship, 📌 Focus Areas), so screen readers skip the decorative
      glyph and read the heading/label text directly. Confirmed in the built
      HTML that the `aria-hidden` attribute survives on the actual headings
      (the TOC's auto-extracted copy drops the attribute since Hugo's TOC
      generator strips attributes when it clones heading text — a cosmetic
      gap only in the nav copy, not the real heading a screen reader lands on).
