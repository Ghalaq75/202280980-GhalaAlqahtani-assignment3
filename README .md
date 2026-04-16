# Ghala Alqahtani – Portfolio (Assignment 3)

**Course:** Software Engineering – Web Development  
**Assignment:** 3 – Advanced Functionality  
**Student ID:** 202280980

---

## Project Description

This assignment builds on the foundations of Assignments 1 and 2, adding advanced JavaScript functionality, external API integrations, complex filtering logic, state management, and performance optimisations.



---

## Features

### Carried over from Assignment 2
- 🌙 **Dark / Light Mode** with localStorage persistence
- ⏰ **Time-based greeting** (Good Morning / Afternoon / Evening)
- 💬 **Inspirational Quote API** (Quotable.io) with fallback + New Quote button
- 🔍 **Live project search** with text highlight
- ✅ **Contact form** with real-time field validation
- 🎯 **Active navigation** highlight on scroll
- 🎞 **Scroll-in animations** via IntersectionObserver

### New in Assignment 3
| # | Feature | Requirement Covered |
|---|---|---|
| 1 | **GitHub Repositories API** – fetches and displays 6 most recent repos with stars, forks, language | API Integration |
| 2 | **Project Filter Buttons** – filter by Java / AI / Design / Research category | Complex Logic |
| 3 | **Sort Dropdown** – sort visible projects A→Z or Z→A | Complex Logic |
| 4 | **Combined Filter + Search + Sort** – all three controls work together seamlessly | Complex Logic |
| 5 | **Subject Dropdown** on contact form – required field with validation | Complex Logic |
| 6 | **Character Counter** – live counter with warning at 90% of limit | State Management |
| 7 | **Personalised Success Message** – "Thank you, [Name]!" after form submit | State Management |
| 8 | **Visit Timer** – shows how long the visitor has been on the page | Timer / Counter |
| 9 | **Mobile Hamburger Menu** – responsive navigation for small screens | Performance / UX |
| 10 | **Back-to-Top Button** – appears after 400 px scroll, smooth scroll to top | UX |
| 11 | **XSS protection** – all API data sanitised with `escapeHTML()` before DOM insertion | Code Quality |
| 12 | **Lazy image loading** + explicit dimensions to prevent layout shift | Performance |

---

## Setup Instructions

### Run locally (no build step required)

```bash
# 1. Clone the repository
git clone https://github.com/ghalaq75/202280980-GhalaAlqahtani-assignment3.git

# 2. Open in your browser
#    Option A – double-click index.html
#    Option B – use a local server (recommended to avoid CORS issues with images)

```

### File structure

```
id-name-assignment3/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── script.js
├── assets/
│   └── images/
│       ├── profile.jpg
│       ├── project1.jpg
│       ├── project2.jpg
│       ├── project3.jpg
│       └── project4.jpg
├── docs/
│   ├── ai-usage-report.md
│   └── technical-documentation.md
├── README.md
└── .gitignore
```


---

## AI Usage Summary

AI tools (Claude and GitHub Copilot) were used to scaffold complex features, suggest error-handling patterns, and assist with documentation. All generated code was reviewed, tested, and modified before inclusion. See [`docs/ai-usage-report.md`](docs/ai-usage-report.md) for full details.

---

## Contact

**Ghala Alqahtani**  
📧 ghalaq75@gmail.com  
📍 Dhahran, Saudi Arabia
