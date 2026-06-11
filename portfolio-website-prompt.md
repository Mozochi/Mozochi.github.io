# Claude Code Prompt — Lewis Jones Portfolio Website

Copy everything below this line into Claude Code.

---

Build me a personal portfolio website from scratch. I'm Lewis Jones, a Computer Science with AI graduate (University of Lincoln, predicted First Class Honours) targeting data engineer / data analyst roles in the UK. The site has two audiences and must work for both: (1) recruiters and HR people who don't read code and need plain-English impact, and (2) technical interviewers who want to see real engineering depth and will click through to GitHub.

## Tech stack & deployment

- **Astro** (static output) + vanilla CSS or Tailwind — your choice, but keep the dependency count minimal. No heavy UI component libraries.
- Must build to a fully static site deployable on **GitHub Pages** (set up the GitHub Actions workflow for deployment from the repo `Mozochi/Mozochi.github.io` or a `gh-pages` branch — include the config and a README explaining how to deploy).
- Lighthouse targets: 95+ across Performance, Accessibility, Best Practices, SEO. No render-blocking junk, fonts loaded with `font-display: swap`, images lazy-loaded.
- Fully responsive, mobile-first. Test layouts at 360px, 768px, 1280px.
- Working dark/light mode toggle that respects `prefers-color-scheme` and persists the choice.

## Design direction — this matters most

The single most important requirement: **this must NOT look like a generic AI-generated portfolio.** I will reject the output if it has any of the following:

- Purple/violet/indigo gradients, or any gradient hero background
- Glassmorphism, frosted-glass cards, floating blurred blobs
- Emoji used as section bullets or decoration (🚀✨💡 etc.)
- Centered hero with "Hi, I'm X 👋 I build things for the web"
- Three-column feature cards with identical icons
- Default Tailwind blue/slate look, or Inter-on-white with no other typographic decisions
- Stock illustration packs (unDraw etc.) or fake browser-window mockups
- Animated particle backgrounds or typing-effect taglines

Instead, design with a clear editorial point of view. Direction to follow:

- **Aesthetic: "data, quietly confident."** Think well-set print: a paper-like off-white background in light mode (e.g. warm `#FAF8F5`-ish), near-black ink text, ONE accent colour used sparingly (a deep teal, burnt orange, or racing green — pick one and commit). Dark mode should be a true considered palette, not just inverted.
- **Typography is the personality.** Pair a characterful display face for headings (e.g. a serif like Fraunces / Newsreader, or a distinctive grotesque like Space Grotesk) with a clean text face, plus a monospace (JetBrains Mono or IBM Plex Mono) used as a *functional accent* — for tags, dates, file-path-style labels like `~/projects/airbnb-price-predictor`, and small metadata. Generous line-height, real typographic hierarchy, large headings that aren't afraid of whitespace.
- **Subtle data-flavoured details, not gimmicks.** Examples: section numbers styled like row indices (`01`, `02`), a thin horizontal rule grid reminiscent of a ledger or terminal output, hover states that underline with the accent colour. One or two small touches max — restraint is the goal.
- Micro-interactions: subtle and fast (150–250ms ease). Respect `prefers-reduced-motion`.
- No more than 2 fonts + 1 mono. No more than 3 colours + neutrals.

## Site structure (single page with anchored sections + one project detail pattern)

### 1. Hero
- Name: **Lewis Jones**
- One-line positioning: "Data engineer in the making — I build pipelines and models in Python and SQL, and explain them in plain English."  (You may improve this line but keep it concrete and modest — no "passionate visionary" language.)
- Location: Nottingham, UK · Open to data engineer / data analyst roles
- Links: GitHub (https://github.com/Mozochi), LinkedIn (https://www.linkedin.com/in/lewis--jones/), Email (lewisjones22183@gmail.com), and a "Download CV" button (placeholder link `/cv.pdf` — I'll drop the file in later).
- Do NOT display a phone number anywhere on the site.

### 2. Projects — the core of the site
Each project gets a card/row with a **two-layer description**: a one-sentence plain-English summary that a non-technical recruiter understands (what it does + why it matters), then a short technical line (stack, architecture) in the mono font, then links. Use this exact content:

**Job Market Pipeline** *(featured, in active development — label it "in progress" honestly)*
- Plain English: "An automated pipeline that collects live job postings, cleans and structures the data, and loads it into a database — so questions like 'which skills are most in demand for data roles?' can be answered with fresh data instead of guesswork."
- Technical: Python · SQL · scheduled ingestion → transformation → warehouse load. (Pull the real README from https://github.com/Mozochi/job-market-pipeline at build time if accessible and refine the wording to match what's actually there; don't invent features that don't exist.)
- Link: GitHub repo.

**Airbnb Price Predictor** *(dissertation project)*
- Plain English: "A machine learning model that predicts the nightly price of an Airbnb listing from its features — built end-to-end: data cleaning, feature engineering, model selection, and evaluation."
- Technical: Python · pandas · scikit-learn.
- Links: GitHub repo + a "Try it live" button for the Streamlit demo. Use a placeholder URL and a clearly-marked TODO comment — the demo is going up on Streamlit Community Cloud soon. Style this button as the primary CTA of the projects section; an interactive demo is the strongest thing on the page for non-technical visitors.

**Bluesky Sentiment Analyser**
- Plain English: "Analyses posts from the Bluesky social network to measure how positive or negative the conversation around a topic is."
- Technical: Python · NLP. Link: https://github.com/Mozochi/bluesky-sentiment-analyser

**MedMCQA LLM Baseline**
- Plain English: "Benchmarks how well large language models answer medical exam questions, establishing a baseline for further research."
- Technical: Python · LLM evaluation. Link: https://github.com/Mozochi/medmcqa-llm-baseline

(Check each repo's README and correct my plain-English summaries if they misrepresent anything. Accuracy over polish.)

### 3. Experience
Concise timeline, same two-audience approach:

- **Data & Engineering Placement — Tillo, Hove (Nov 2025).** Worked daily with the data engineering team in Python and SQL alongside cloud analytics and database tooling. Delivered a machine learning project on internal data from initial brief to a finished, documented model presented to the team. Contributed to standups, retros and sprint planning in an Agile environment.
- **Data & BI Work Experience — Boots UK, Nottingham (May 2026).** Shadowed a data analyst using Power BI to track chilled food sales and target stock distribution across stores; saw how commercial data feeds product and supply decisions at a major UK retailer.
- **Customer Team Member — Co-op, Nottingham (2024–2025).** Increased average weekly membership signups by 25% through targeted customer engagement; helped cut high-value stock wastage by ~30% in two months.
- **Education:** BSc (Hons) Computer Science with AI, University of Lincoln, 2023–2026 — predicted First Class Honours. Dissertation: the Airbnb price predictor above.

### 4. Skills
Not a wall of logos. Group them honestly with a one-line context each, e.g.:
- **Python** (pandas, scikit-learn, PyTorch) — daily driver on placement and throughout degree
- **SQL** — joins, aggregates, subqueries; used commercially at Tillo
- **Power BI** — building dashboards on real datasets
- **Git & GitHub, Linux, MySQL, R** — supporting toolkit

### 5. Footer / contact
Short. "The best way to reach me is email or LinkedIn." Repeat the three links. Small mono-font easter-egg line is fine (e.g. `built by hand, no template — view source on GitHub`), nothing cringe.

## Content & SEO

- `<title>`: "Lewis Jones — Data Engineer | Python, SQL, Machine Learning"
- Proper meta description, Open Graph tags, favicon (generate a simple monogram "LJ" SVG favicon matching the accent colour).
- Semantic HTML throughout (`<main>`, `<section>`, `<nav>`, heading hierarchy), alt text on everything, visible focus states, AA contrast minimum in both themes.
- British English spelling throughout.

## Process

1. Scaffold the project and show me the colour palette + font pairing choice first as a quick summary before building everything out.
2. Build section by section. After each section, do a self-review pass against the "must NOT look like" list above.
3. Finish with: a README covering local dev (`npm run dev`) and GitHub Pages deployment, and a list of the TODOs I need to fill in (CV pdf, Streamlit URL).

Quality bar: if a stranger saw this site with the name removed, they should think "a careful person who works with data made this," not "an AI made this in one prompt."
