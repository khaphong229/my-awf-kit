---
name: md-to-html-neo
description: Convert Markdown files into stunning Neo-Cyberpunk HTML pages inspired by tensorship.tech. Dark mode only, orange accent, blue glow, Be Vietnam Pro font. Content preserved 100%.
risk: safe
date_added: "2026-04-17"
---

# Markdown → HTML Neo-Cyberpunk Renderer

Convert Markdown into a **premium dark-mode HTML page** with Neo-Cyberpunk aesthetics inspired by [tensorship.tech](https://course.tensorship.tech/). Single file, zero dependencies, 100% content fidelity.

## When to Use This Skill

- User wants to convert `.md` to HTML with **Tensorship-style** design
- User says `/render-neo`, "render neo", "tensorship style"
- User wants a dark, premium reading experience for study materials

## Core Principles

1. **Zero Dependencies** — Single HTML file with inline CSS/JS. No npm, no CDN, no build tools.
2. **100% Content Fidelity** — NEVER add, remove, or modify any content. NON-NEGOTIABLE.
3. **Dark Mode Only** — No light mode toggle. Pure dark experience like tensorship.tech.
4. **Responsive** — Reads perfectly on mobile, tablet, and desktop.
5. **Premium Feel** — Blue glow border, orange accents, smooth animations.

---

## ⛔ CONTENT RULES (CRITICAL — READ THIS FIRST)

```
❌ ABSOLUTELY FORBIDDEN:
- Adding text, explanations, or commentary not in the original markdown
- Removing or omitting ANY content (even if it seems redundant)
- Fixing typos, grammar, or wording
- Adding images, icons, or illustrations not in the original
- Reordering sections or paragraphs
- Translating any content
- Summarizing or paraphrasing

✅ ALLOWED:
- Converting markdown syntax → HTML elements
- Adding CSS for styling (fonts, colors, spacing, borders)
- Adding JS for UI features (TOC nav, progress bar, scroll-to-top, copy code)
- Rendering emoji that exist in the original markdown
- Adding structural HTML (nav, header, footer, wrapper divs)
- Adding `id` attributes to headings for anchor navigation
```

**Verification:** After generating, mentally verify: "If I strip all HTML tags and CSS/JS, does the remaining text match the source markdown exactly?"

---

## Design System

### Typography

```css
/* Font — Be Vietnam Pro from Google Fonts */
/* A modern Vietnamese-optimized sans-serif */
/* Code: JetBrains Mono */

--font-main: 'Be Vietnam Pro', sans-serif;
--font-mono: 'JetBrains Mono', monospace;

/* Scale — fluid with clamp() */
--fs-h1: clamp(2rem, 5vw, 3rem);
--fs-h2: clamp(1.5rem, 3.5vw, 2rem);
--fs-h3: clamp(1.2rem, 2.5vw, 1.5rem);
--fs-h4: clamp(1rem, 2vw, 1.2rem);
--fs-body: clamp(0.95rem, 1.5vw, 1.05rem);
--fs-small: clamp(0.8rem, 1.2vw, 0.875rem);
--fs-code: clamp(0.82rem, 1.3vw, 0.92rem);

/* Weight */
--fw-heading: 800;
--fw-subheading: 700;
--fw-body: 400;
--fw-bold: 600;

/* Line height */
--lh-heading: 1.25;
--lh-body: 1.75;
--lh-code: 1.6;

/* Letter spacing */
--ls-heading: -0.02em;  /* Tight tracking for headings */
--ls-body: 0;
```

### Color Palette — Dark Mode (ONLY mode)

```css
:root {
  /* Backgrounds — Deep black with warmth */
  --bg-body: #0f0f0f;
  --bg-container: #1a1a1a;
  --bg-card: #2a2a2a;
  --bg-code: #1e1e1e;
  --bg-code-inline: #2a2a2a;
  --bg-table-header: #252525;
  --bg-table-alt: #1e1e1e;
  --bg-blockquote: rgba(255, 87, 34, 0.04);

  /* Accent — Deep Orange (Tensorship signature) */
  --accent: #ff5722;
  --accent-light: #ff8a65;
  --accent-dark: #e64a19;
  --accent-glow: rgba(255, 87, 34, 0.15);
  --accent-subtle: rgba(255, 87, 34, 0.08);

  /* Blue Glow (Tensorship border effect) */
  --glow-blue: rgba(0, 71, 171, 0.4);
  --glow-blue-subtle: rgba(0, 71, 171, 0.2);

  /* Text */
  --text-primary: #ffffff;
  --text-secondary: #a0a0a0;
  --text-muted: #787878;
  --text-heading: #ffffff;
  --text-link: #ff8a65;
  --text-link-hover: #ffab91;

  /* Borders */
  --border: rgba(255, 255, 255, 0.08);
  --border-strong: rgba(255, 255, 255, 0.15);
  --border-accent: rgba(255, 87, 34, 0.3);

  /* Shadows */
  --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.4);
  --shadow-lg: 0 8px 24px rgba(0, 0, 0, 0.5);
  --shadow-glow: 0 0 30px var(--glow-blue);

  /* Scrollbar */
  --scrollbar-track: #1a1a1a;
  --scrollbar-thumb: #333333;
  --scrollbar-thumb-hover: #555555;

  /* Progress bar */
  --progress-fill: var(--accent);

  /* Radius */
  --radius-sm: 6px;
  --radius-md: 12px;
  --radius-lg: 16px;

  /* Transition */
  --ease: cubic-bezier(.4, 0, .2, 1);
  --duration: 0.3s;
}
```

### Element Styling Reference

| Element | Style Notes |
|---------|------------|
| `body` | bg `#0f0f0f`, radial-gradient subtle warm glow center |
| `.container` | bg `#1a1a1a`, `box-shadow: 0 0 30px rgba(0,71,171,0.4)` (blue glow!), border `rgba(255,255,255,0.08)`, `border-radius: 12px`, max-width 900px |
| `h1` | Font weight 800, letter-spacing tight, white. **No decoration**. Large, bold, commanding. |
| `h2` | Font weight 700, left border 4px `--accent`, padding-left 16px. Uppercase sometimes. |
| `h3` | Font weight 700, white, slightly smaller. Subtle bottom margin. |
| `h4` | Font weight 600, `--text-secondary` color, no decorations |
| `<hr>` | Gradient line `--accent → transparent`, 1px height, 3rem margin |
| `<table>` | Full-width, header row bg `#252525`, alt rows `#1e1e1e`, border `--border`, rounded corners on wrapper |
| `<code>` inline | bg `#2a2a2a`, border `--border`, border-radius 4px, padding 2px 8px, font-mono, color `--accent-light` |
| `<pre><code>` | bg `#1e1e1e`, border-radius 8px, padding 1.5rem, border-left 3px `--accent`, overflow-x auto. **Copy button** top-right. |
| `<blockquote>` | border-left 4px `--accent`, bg `rgba(255,87,34,0.04)`, padding 1rem 1.5rem, italic, `--text-secondary` |
| `<a>` | color `--accent-light`, no underline default, underline on hover |
| `<ul>/<ol>` | Custom markers colored `--accent`, comfortable spacing (0.5rem between items) |
| `<checkbox>` | Styled with accent color for checked state |
| ASCII art blocks | Monospace, bg-code, NO wrapping, `white-space: pre`, smaller font, centered, horizontal scroll |
| `<img>` | max-width 100%, rounded corners, centered |
| **Section numbers** | If heading starts with emoji+number (like "1️⃣"), style the number/emoji larger |

---

## HTML Template Structure

```html
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{DOCUMENT_TITLE}</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    /* === RESET === */
    /* === CSS VARIABLES === */
    /* === BODY (radial gradient bg) === */
    /* === CONTAINER (blue glow box-shadow) === */
    /* === TYPOGRAPHY === */
    /* === COMPONENTS (tables, code, blockquotes, lists, checkboxes) === */
    /* === COPY BUTTON for code blocks === */
    /* === TABLE OF CONTENTS SIDEBAR === */
    /* === PROGRESS BAR (bottom, orange) === */
    /* === SCROLL TO TOP === */
    /* === RESPONSIVE === */
    /* === PRINT === */
    /* === SCROLLBAR === */
    /* === ANIMATIONS (fade-in, slide-up) === */
  </style>
</head>
<body>
  <!-- Table of Contents (sidebar on desktop, hamburger on mobile) -->
  <nav class="toc" id="toc">
    <h3 class="toc-title">Mục lục</h3>
    <ul>
      <!-- Auto-generated from h2/h3 headings -->
    </ul>
  </nav>

  <!-- TOC Toggle Button (mobile only) -->
  <button class="toc-toggle" id="tocToggle" aria-label="Toggle table of contents">
    <!-- Hamburger icon SVG -->
  </button>

  <!-- Main Content Container with blue glow -->
  <main class="container">
    <article class="content">
      <!-- CONVERTED MARKDOWN CONTENT HERE -->
    </article>
  </main>

  <!-- Scroll to Top -->
  <button class="scroll-top" id="scrollTop" aria-label="Scroll to top">↑</button>

  <!-- Reading Progress Bar (BOTTOM) -->
  <div class="progress-bar" id="progressBar"></div>

  <script>
    /* === READING PROGRESS BAR (bottom position) === */
    /* === SCROLL TO TOP VISIBILITY === */
    /* === TOC ACTIVE STATE (Intersection Observer) === */
    /* === TOC MOBILE TOGGLE === */
    /* === SMOOTH SCROLL === */
    /* === COPY CODE BUTTON === */
    /* === FADE-IN ANIMATION ON SCROLL === */
  </script>
</body>
</html>
```

---

## Key Design Differences from md-to-html (original)

| Feature | md-to-html (original) | md-to-html-neo (this) |
|---------|----------------------|----------------------|
| Theme | Dark + Light toggle | **Dark only** |
| Font | Outfit + Inter | **Be Vietnam Pro** |
| Accent | Indigo `#6c63ff` | **Orange `#ff5722`** |
| Heading style | Gradient underline | **Bold 800, tight tracking** |
| Progress bar | Top of page | **Bottom of page** |
| Container | No glow | **Blue glow border** |
| Body BG | Flat `#0f1117` | **Radial gradient `#0f0f0f`** |
| Code blocks | Basic dark | **Dark + Copy button + accent border** |
| Overall vibe | Clean minimal | **Neo-Cyberpunk / AI Aesthetic** |

---

## Markdown → HTML Conversion Rules

### Headings
```
# H1    → <h1 id="slugified-text">text</h1>
## H2   → <h2 id="slugified-text">text</h2>
### H3  → <h3 id="slugified-text">text</h3>
#### H4 → <h4 id="slugified-text">text</h4>
```
- Generate IDs by slugifying: lowercase, remove special chars, spaces → hyphens
- Add all h2/h3 to Table of Contents

### Inline Formatting
```
**bold**       → <strong>bold</strong>
*italic*       → <em>italic</em>
`code`         → <code class="inline-code">code</code>
[text](url)    → <a href="url" target="_blank" rel="noopener">text</a>
~~strike~~     → <del>strike</del>
```

### Code Blocks
````
```language
code here
```
````
→ Wrap in `<div class="code-block">` with:
  - `<div class="code-header"><span class="code-lang">language</span><button class="copy-btn">Copy</button></div>`
  - `<pre><code class="lang-{language}">code here</code></pre>`
- For ASCII art / diagram blocks (no language): monospace, prevent wrapping, `white-space: pre`

### Tables
```
| H1 | H2 |
|----|------|
| A  | B   |
```
→ Wrap in `<div class="table-wrapper">`, `<table>` with `<thead>` and `<tbody>`

### Lists
```
- item    → <ul><li>item</li></ul>
1. item   → <ol><li>item</li></ol>
- [ ] item → <li class="task-item"><input type="checkbox" disabled> item</li>
- [x] item → <li class="task-item"><input type="checkbox" checked disabled> item</li>
```

### Blockquotes
```
> text → <blockquote><p>text</p></blockquote>
```
- Multi-level: nest `<blockquote>`
- Special: `> **keyword:**` → add accent highlight class

### Horizontal Rules
```
---  → <hr>
```

### Images
```
![alt](src) → <figure><img src="src" alt="alt" loading="lazy"><figcaption>alt</figcaption></figure>
```

---

## JavaScript Features

### 1. Reading Progress Bar (BOTTOM)
```javascript
// Thin bar FIXED at BOTTOM of page
// Width: 0% at top → 100% at bottom
// Background: var(--accent) solid orange
// Height: 3px, z-index high
// Position: fixed, bottom: 0, left: 0
```

### 2. Table of Contents
```javascript
// Auto-generated from h2 and h3 in the content
// Desktop: fixed sidebar left (width ~260px)
// Mobile: hidden by default, hamburger toggle
// Active state: highlight current section (IntersectionObserver)
// Click: smooth scroll to section
// Active item has left border accent + bg accent-subtle
```

### 3. Scroll to Top
```javascript
// Appears when scrolled past 300px
// Smooth scroll to top on click
// Styled: accent bg, white text, circular
// Fade in/out animation
```

### 4. Copy Code Button
```javascript
// Each code block has a "Copy" button in top-right
// Click → copy code to clipboard
// Show "Copied!" feedback for 2 seconds
// Styled: subtle bg, accent on hover
```

### 5. Smooth Scroll
```javascript
// All anchor links use smooth scrolling
// Offset for fixed elements
```

### 6. Fade-in Animations
```javascript
// Sections fade in as they enter viewport
// Using IntersectionObserver
// Animation: opacity 0 → 1, translateY(20px) → 0
// Duration: 0.6s with var(--ease)
```

---

## Generation Workflow

### Step 1: Read the Markdown File
```
Read the entire .md file content
Note the document title (first h1, or filename)
Count sections for complexity estimation
```

### Step 2: Convert Content
```
Parse markdown → HTML following the conversion rules above
Generate heading IDs for TOC
Build TOC from h2/h3 headings
DO NOT modify any text content
```

### Step 3: Assemble HTML
```
Use the HTML template structure
Inject: CSS variables, component styles, converted content, TOC, JS
Apply blue glow to container
Place progress bar at BOTTOM
```

### Step 4: Write Output
```
Output filename: same as input, with .neo.html extension
Output location: same directory as input
Example: docs/learn/day-00.md → docs/learn/day-00.neo.html
```

### Step 5: Deliver
```
Open the HTML file in the browser or tell user the path
Tell the user:
  - File location
  - How to navigate: TOC sidebar, scroll to top
  - The Neo-Cyberpunk aesthetic features
```

---

## Quality Checklist

Before delivering, verify:

- [ ] **Content matches 100%** — no additions, no omissions
- [ ] **All headings have IDs** — TOC links work
- [ ] **Code blocks with Copy button** — functional
- [ ] **Tables are responsive** — horizontal scroll on narrow screens
- [ ] **ASCII art preserved** — monospace, no wrapping, `white-space: pre`
- [ ] **Blue glow on container** — visible
- [ ] **Progress bar at BOTTOM** — orange, moves on scroll
- [ ] **Mobile responsive** — readable at 375px width
- [ ] **Be Vietnam Pro font loads** — headings look bold and tight
- [ ] **Orange accent throughout** — links, borders, markers, highlights
- [ ] **No external dependencies** — works offline (except Google Fonts)
- [ ] **Checkboxes rendered** — `- [ ]` and `- [x]` display correctly

---

## Tips

1. **ASCII diagrams common**: Technical docs often use box-drawing characters — MUST preserve exact spacing
2. **Emoji-heavy headings**: Keep emoji, they add visual character
3. **Long tables**: Ensure table wrapper allows horizontal scroll
4. **Nested lists**: Multiple indentation levels should be styled differently
5. **Code-heavy docs**: Generous padding, copy buttons, accent left border
