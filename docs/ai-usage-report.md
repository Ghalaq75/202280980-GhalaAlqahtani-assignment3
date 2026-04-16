# AI Usage Report – Assignment 3

**Student:** Ghala Alqahtani  
**Course:** Software Engineering – Web Development  
**Assignment:** 3 – Advanced Functionality

---

## 1. Tools Used & Use Cases

| Tool | How It Was Used |
|------|-----------------|
| **Claude (Anthropic)** | Primary assistant for code generation, architecture planning, debugging, and documentation writing |
| **GitHub Copilot** | Inline code completion while writing the filter/sort logic and GitHub API integration |

### Claude – Specific Use Cases

- **GitHub API integration:** Asked Claude to explain the GitHub REST API (`/users/:username/repos`) response shape and generate a `buildRepoCard()` function. The output was reviewed and modified to add XSS escaping via `escapeHTML()` and demo fallback cards.
- **Filter + Sort logic:** Prompted Claude to suggest how to combine a category filter with a live search and a sort dropdown in a single `applyFiltersAndSort()` function. The generated code was refactored to use a shared `activeFilter` state variable.
- **Mobile hamburger nav:** Asked for a CSS + JS approach that avoids external libraries. Claude suggested toggling a CSS class; the animation keyframes were customised manually.
- **Character counter:** Claude provided the initial `input` event listener; the warning threshold (`>= 90%`) was adjusted and the CSS `.warn` colour was chosen to match the existing error palette.
- **Documentation:** README.md and this report structure were drafted with Claude's assistance, then rewritten in first person and expanded with personal reflections.

### GitHub Copilot – Specific Use Cases

- Autocomplete for repetitive DOM queries (`document.getElementById`, `addEventListener` chains).
- Suggested the `escapeRegex` helper pattern when implementing the highlight feature.

---

## 2. Benefits & Challenges

### Benefits
- **Speed:** Complex features like the GitHub API card renderer and the combined filter/sort function were scaffolded in minutes instead of hours.
- **Error handling patterns:** Claude consistently reminded me to add `try/catch` blocks and provide user-friendly fallback states when APIs fail – a practice I reinforced throughout the codebase.
- **Code clarity:** AI suggestions often came with JSDoc comments, which improved the overall documentation quality.

### Challenges
- **Hallucinated API endpoints:** Claude initially suggested `https://zenquotes.io/api/random` which has CORS restrictions. I had to verify the correct endpoint (`api.quotable.io`) independently and update the code.
- **Over-engineering:** The first draft of the filter function was overly complex (using a `Map` for indexing). I simplified it to a straightforward `Array.forEach` loop that is easier to read and debug.
- **Generic styling:** Copilot's style suggestions used generic class names that conflicted with the existing CSS custom properties. All styling had to be reviewed against the `styles.css` variable system.

---

## 3. Learning Outcomes

- Gained confidence in consuming REST APIs with `fetch`, `async/await`, and proper error handling patterns.
- Understood the importance of input sanitisation (`escapeHTML`) when inserting API-sourced data into the DOM.
- Learned to use `IntersectionObserver` for performance-efficient scroll animations rather than listening on the `scroll` event directly.
- Improved understanding of JavaScript state management: using a module-level variable (`activeFilter`) to coordinate multiple UI controls without a framework.
- Developed a workflow of **prompt → review → test → refine** rather than blindly accepting AI output.

---

## 4. Responsible Use & Modifications

All AI-generated code went through the following process before being included:

1. **Read and understand** every line – no code was included that I could not explain.
2. **Test in the browser** – each feature was checked for functionality and edge cases (empty API responses, network errors, empty search queries).
3. **Modify for context** – variable names, comments, and structure were aligned with the existing Assignment 2 codebase conventions.
4. **Remove unnecessary complexity** – any generated abstractions that were not needed for this scope were stripped out.
5. **Document changes** – meaningful commit messages described what was AI-assisted and what was manually written.

AI was used as a **learning tool and productivity aid**, not as a replacement for understanding the material.
