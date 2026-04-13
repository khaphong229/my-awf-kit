---
name: md-to-html
description: Convert Markdown files into beautiful, single-file HTML pages for visual reading. Content is preserved 100% — only the presentation format changes.
risk: safe
date_added: "2026-04-09"
---

# Markdown → HTML Renderer

Convert any Markdown document into a stunning, single-file HTML page optimized for reading and learning. **Zero dependencies, zero content changes.**

## When to Use This Skill

- User wants to convert a `.md` file to a visually beautiful `.html` page
- User says `/render`, "chuyển sang HTML", "render markdown", "tạo HTML từ markdown"
- User wants a more comfortable reading experience for documentation or study materials

## Core Principles

1. **Zero Dependencies** — Single HTML file with inline CSS/JS. No npm, no CDN, no build tools.
2. **100% Content Fidelity** — NEVER add, remove, or modify any content from the source markdown. This is NON-NEGOTIABLE.
3. **Dark Mode Default** — Ships with dark mode on, with a toggle to switch to light mode.
4. **Responsive** — Reads perfectly on mobile, tablet, and desktop.
5. **Print-friendly** — `@media print` styles included.

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
- Converting markdown syntax → HTML elements (headings, lists, tables, code blocks etc.)
- Adding CSS for styling (fonts, colors, spacing, borders)
- Adding JS for UI features (TOC nav, dark/light toggle, scroll-to-top, progress bar)
- Rendering emoji that exist in the original markdown
- Adding structural HTML (nav, header, footer, wrapper divs) for layout
- Adding `id` attributes to headings for anchor navigation
```

**Verification:** After generating, the AI MUST mentally verify: "If I strip all HTML tags and CSS/JS, does the remaining text match the source markdown exactly?"

---

## Design System

### Typography

```css
/* Fonts — load from Google Fonts */
/* Heading: Outfit (modern, geometric, clean) */
/* Body: Inter (highly readable, excellent for long-form) */
/* Code: JetBrains Mono (ligatures, dev-friendly) */

--font-heading: 'Outfit', sans-serif;
--font-body: 'Inter', sans-serif;
--font-mono: 'JetBrains Mono', monospace;

/* Scale */
--fs-h1: clamp(1.8rem, 4vw, 2.5rem);
--fs-h2: clamp(1.4rem, 3vw, 1.85rem);
--fs-h3: clamp(1.15rem, 2.5vw, 1.45rem);
--fs-h4: clamp(1rem, 2vw, 1.2rem);
--fs-body: clamp(0.95rem, 1.5vw, 1.05rem);
--fs-small: clamp(0.8rem, 1.2vw, 0.875rem);
--fs-code: clamp(0.82rem, 1.3vw, 0.92rem);

/* Line height */
--lh-heading: 1.3;
--lh-body: 1.75;
--lh-code: 1.6;
```

### Color Palette — Dark Mode (Default)

```css
:root {
  /* Background layers */
  --bg-primary: #0f1117;
  --bg-secondary: #161822;
  --bg-tertiary: #1c1f2e;
  --bg-code: #1a1d2e;
  --bg-code-inline: #252840;
  --bg-table-alt: #181b28;
  --bg-blockquote: #1a1e30;

  /* Text */
  --text-primary: #e2e4ed;
  --text-secondary: #9ba1b5;
  --text-heading: #f0f2f8;
  --text-link: #6ea8fe;
  --text-link-hover: #93c0ff;

  /* Accents */
  --accent-primary: #6c63ff;
  --accent-secondary: #38bdf8;
  --accent-green: #4ade80;
  --accent-yellow: #fbbf24;
  --accent-red: #f87171;
  --accent-orange: #fb923c;

  /* Borders & Dividers */
  --border-color: #2a2d3e;
  --border-subtle: #222538;
  --divider: #2a2d3e;

  /* Shadows */
  --shadow-sm: 0 1px 3px rgba(0,0,0,0.3);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.4);
  --shadow-lg: 0 8px 24px rgba(0,0,0,0.5);

  /* Scrollbar */
  --scrollbar-track: #161822;
  --scrollbar-thumb: #2a2d3e;

  /* Progress bar */
  --progress-bg: transparent;
  --progress-fill: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
}
```

### Color Palette — Light Mode

```css
[data-theme="light"] {
  --bg-primary: #ffffff;
  --bg-secondary: #f8f9fc;
  --bg-tertiary: #f1f3f8;
  --bg-code: #f6f7fb;
  --bg-code-inline: #eef0f7;
  --bg-table-alt: #f8f9fc;
  --bg-blockquote: #f0f4ff;

  --text-primary: #1e293b;
  --text-secondary: #64748b;
  --text-heading: #0f172a;
  --text-link: #4f46e5;
  --text-link-hover: #3730a3;

  --accent-primary: #4f46e5;
  --accent-secondary: #0ea5e9;

  --border-color: #e2e8f0;
  --border-subtle: #f1f5f9;
  --divider: #e2e8f0;

  --shadow-sm: 0 1px 3px rgba(0,0,0,0.06);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.08);
  --shadow-lg: 0 8px 24px rgba(0,0,0,0.1);

  --scrollbar-track: #f1f5f9;
  --scrollbar-thumb: #cbd5e1;
}
```

### Element Styling Reference

| Element | Style Notes |
|---------|------------|
| `h1` | Font Outfit, gradient underline accent, extra top margin |
| `h2` | Left border accent (4px, accent-primary), padding-left |
| `h3` | Subtle bottom border, slightly lighter color |
| `h4` | No decorations, just weight + size difference |
| `<hr>` | Gradient line (accent-primary → transparent), 3rem margin |
| `<table>` | Full-width, border-collapse, alternating row bg, rounded corners on wrapper |
| `<code>` inline | bg-code-inline, border-radius 4px, padding 2px 6px, font-mono |
| `<pre><code>` | bg-code, border-radius 8px, padding 1.25rem, overflow-x auto, border-left 3px accent |
| `<blockquote>` | bg-blockquote, border-left 4px accent, padding 1rem 1.5rem, italic |
| `<a>` | text-link color, underline on hover, smooth transition |
| `<ul>/<ol>` | Custom markers (accent colored), comfortable spacing |
| `<checkbox>` `- [ ]` / `- [x]` | Styled checkbox icons, green for checked |
| ASCII art blocks | Monospace, bg-code, centered, no wrapping, smaller font |
| `<img>` | max-width 100%, rounded corners, centered, shadow |

---

## HTML Template Structure

```html
<!DOCTYPE html>
<html lang="vi" data-theme="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{DOCUMENT_TITLE}</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&family=Outfit:wght@500;600;700&display=swap" rel="stylesheet">
  <style>
    /* === RESET === */
    /* === CSS VARIABLES (dark + light) === */
    /* === LAYOUT === */
    /* === TYPOGRAPHY === */
    /* === COMPONENTS (tables, code, blockquotes, lists, checkboxes) === */
    /* === TABLE OF CONTENTS SIDEBAR === */
    /* === PROGRESS BAR === */
    /* === THEME TOGGLE === */
    /* === SCROLL TO TOP === */
    /* === RESPONSIVE === */
    /* === PRINT === */
    /* === ANIMATIONS === */
  </style>
</head>
<body>
  <!-- Reading Progress Bar -->
  <div class="progress-bar" id="progressBar"></div>

  <!-- Theme Toggle (top-right floating) -->
  <button class="theme-toggle" id="themeToggle" aria-label="Toggle theme">
    <!-- Sun/Moon icon SVG -->
  </button>

  <!-- Table of Contents (sidebar on desktop, hamburger on mobile) -->
  <nav class="toc" id="toc">
    <h3 class="toc-title">Mục lục</h3>
    <ul>
      <!-- Auto-generated from headings -->
    </ul>
  </nav>

  <!-- TOC Toggle Button (mobile only) -->
  <button class="toc-toggle" id="tocToggle" aria-label="Toggle table of contents">
    <!-- Hamburger icon SVG -->
  </button>

  <!-- Main Content -->
  <main class="content">
    <article>
      <!-- CONVERTED MARKDOWN CONTENT HERE -->
    </article>
  </main>

  <!-- Scroll to Top -->
  <button class="scroll-top" id="scrollTop" aria-label="Scroll to top">↑</button>

  <script>
    /* === THEME TOGGLE === */
    /* === READING PROGRESS BAR === */
    /* === SCROLL TO TOP VISIBILITY === */
    /* === TOC ACTIVE STATE (Intersection Observer) === */
    /* === TOC MOBILE TOGGLE === */
    /* === SMOOTH SCROLL === */
  </script>
</body>
</html>
```

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
→ `<pre><code class="lang-{language}">code here</code></pre>`

- Apply basic syntax highlighting via CSS classes if language is specified
- For ASCII art / diagram blocks (no language specified): use monospace, prevent wrapping, center

### Tables
```
| H1 | H2 |
|----|----|
| A  | B  |
```
→ Wrap in `<div class="table-wrapper">` for horizontal scroll on mobile
→ `<table>` with `<thead>` and `<tbody>`

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
- Multi-level blockquotes: nest `<blockquote>` elements
- Special: `> **keyword:**` at start → add accent color class

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

### 1. Reading Progress Bar
```javascript
// Thin bar at top of page showing scroll progress
// Width: 0% at top → 100% at bottom
// Style: gradient (accent-primary → accent-secondary)
// Height: 3px, fixed top, z-index high
```

### 2. Theme Toggle
```javascript
// Toggle between data-theme="dark" and data-theme="light"
// Save preference to localStorage
// Load saved preference on page load (default: dark)
// Animate icon transition (sun ↔ moon)
```

### 3. Table of Contents
```javascript
// Auto-generated from h2 and h3 in the content
// Desktop: fixed sidebar left (width ~260px)
// Mobile: hidden by default, hamburger toggle
// Active state: highlight current section using IntersectionObserver
// Click: smooth scroll to section
```

### 4. Scroll to Top
```javascript
// Appears when scrolled past 300px
// Smooth scroll to top on click
// Fade in/out animation
```

### 5. Smooth Scroll
```javascript
// All anchor links use smooth scrolling
// Offset for fixed elements (progress bar)
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
```

### Step 4: Write Output
```
Output filename: same as input, with .html extension
Output location: same directory as input
Example: docs/learn/day-00.md → docs/learn/day-00.html
```

### Step 5: Deliver
```
Open the HTML file in the browser
Tell the user:
  - File location
  - Keyboard shortcuts: scroll, theme toggle
  - How to customize: CSS variables in :root
```

---

## Quality Checklist

Before delivering, verify:

- [ ] **Content matches 100%** — no additions, no omissions
- [ ] **All headings have IDs** — TOC links work
- [ ] **Code blocks render correctly** — monospace, proper background
- [ ] **Tables are responsive** — horizontal scroll on narrow screens
- [ ] **ASCII art preserved** — monospace, no wrapping
- [ ] **Dark mode is default** — looks good
- [ ] **Light mode works** — toggle switch functions
- [ ] **Progress bar works** — moves on scroll
- [ ] **Mobile responsive** — readable at 375px width
- [ ] **No external dependencies** — works offline (except Google Fonts, which degrades gracefully)
- [ ] **Checkboxes rendered** — `- [ ]` and `- [x]` display correctly

---

## Tips

1. **Long documents:** For very long markdown (500+ lines), consider adding a "Back to TOC" floating button
2. **Code-heavy docs:** Ensure code blocks have generous padding and clear background contrast
3. **Table-heavy docs:** Make sure table wrapper allows horizontal scroll
4. **ASCII diagrams:** These are common in technical docs — preserve exact spacing with `white-space: pre`
5. **Emoji:** Keep all emoji from the source, they add visual interest
