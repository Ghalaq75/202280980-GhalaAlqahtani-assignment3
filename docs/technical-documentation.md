# Technical Documentation – Assignment 3

**Project:** Ghala Alqahtani Portfolio  
**Assignment:** 3 – Advanced Functionality  
**Tech Stack:** HTML5 · CSS3 (custom properties) · Vanilla JavaScript (ES2022)

---

## Architecture Overview

```
id-name-assignment3/
├── index.html                        # Single-page application shell
├── css/
│   └── styles.css                    # All styles; CSS variables for light/dark theme
├── js/
│   └── script.js                     # All JavaScript; modular functions, no frameworks
├── assets/
│   └── images/                       # profile.jpg, project1–4.jpg (optimised)
├── docs/
│   ├── ai-usage-report.md
│   └── technical-documentation.md
├── README.md
└── .gitignore
```

---

## Features & Implementation Details

### 1. Theme Toggle (State Management)
- Reads `localStorage.getItem('theme')` on load; falls back to `prefers-color-scheme`.
- CSS `[data-theme="dark"]` selector swaps all CSS variable values at once — no per-element JS needed.

### 2. Time-Based Greeting
- Reads `new Date().getHours()` → "Good Morning / Afternoon / Evening".

### 3. Inspirational Quote API
- **Endpoint:** `https://api.quotable.io/random?tags=inspirational|wisdom`
- 6-second `AbortSignal.timeout`; 7 local fallback quotes on failure.
- UI states: loading dots → quote → error + retry.

### 4. GitHub Repositories API (NEW – A3)
- **Endpoint:** `https://api.github.com/users/{username}/repos?sort=updated&per_page=6`
- Shows: name (linked), description, language, stars, forks, last-updated date.
- All API data sanitised with `escapeHTML()` before DOM insertion (XSS prevention).
- Fallback: 4 demo repo cards if API fails.

### 5. Project Filter + Sort (NEW – A3)
- Category buttons set `activeFilter` module variable.
- Search input + sort dropdown all call the same `applyFiltersAndSort()` function.
- Steps applied in order: category filter → keyword search → alphabetical sort.

### 6. Character Counter (NEW – A3)
- Live `current / 500` counter on the message textarea.
- CSS `.warn` class (red) triggers at ≥ 90% of the character limit.

### 7. Contact Form Validation (Enhanced – A3)
- Four fields validated simultaneously on submit (all errors shown at once).
- On success: visitor's first name saved to `localStorage`; personalised "Thank you, [Name]!" message displayed.

### 8. Site Visit Timer (NEW – A3)
- `setInterval` increments every 1000 ms; displays `Xs` or `Xm Ys`.
- `aria-live="polite"` for screen reader accessibility.

### 9. Mobile Hamburger Navigation (NEW – A3)
- CSS class toggle shows/hides nav links on small screens.
- `aria-expanded` updated; menu closes on any link click.

### 10. Back-to-Top Button (NEW – A3)
- Fades in after 400 px scroll; smooth scrolls to top.

---

## Performance Testing — Lighthouse Results

> Tested via Chrome DevTools → Lighthouse (Desktop, Incognito)

| Category | Score |
|---|---|
| Performance | 96 |
| Accessibility | 98 |
| Best Practices | 100 |
| SEO | 100 |

### Optimisations Applied Based on Lighthouse

| Lighthouse Issue | Fix |
|---|---|
| Images cause layout shift (CLS) | `width="200" height="200"` on profile image |
| Off-screen images slow load | `loading="lazy"` on all images |
| Scroll event listeners block thread | `{ passive: true }` on all scroll listeners |
| External libraries add weight | Zero dependencies — vanilla JS only |
| Missing meta description | `<meta name="description">` added to `<head>` |

### How to Run Lighthouse
1. Open site in **Chrome Incognito**
2. DevTools (`F12`) → **Lighthouse** tab
3. Select: Desktop · All categories · Clear storage
4. Click **Analyze page load**

---

## API Error Handling Pattern

```
1. Show loading indicator
2. fetch() with AbortSignal.timeout(6000)
3a. Success → parse JSON → render content
3b. Failure → console.warn → render fallback (user never sees an empty section)
```

---

## State Management Summary

| State | Storage | Purpose |
|---|---|---|
| Theme | `localStorage` | Persists across visits |
| Visitor name | `localStorage` | Personalised success message |
| Active filter | JS variable | Coordinates filter + search + sort |
| Timer seconds | JS variable | Incremented by setInterval |
| Form status | DOM class `.show` | Shows/hides success message |

---

## Browser Compatibility

Chrome 120+, Firefox 121+, Safari 17+, Edge 120+, iOS Safari 17, Android Chrome 120

---

## Code Quality Checklist

- [x] JSDoc comment on every function
- [x] CSS custom properties for all colours/spacing — no magic numbers
- [x] No unused CSS or JS
- [x] `'use strict'` at top of script.js
- [x] All API data sanitised with `escapeHTML()` before DOM insertion
- [x] Consistent 4-space indentation
- [x] Descriptive variable and function names
- [x] No broken links or missing assets
