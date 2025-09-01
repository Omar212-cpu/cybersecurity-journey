# DOM-Based Attacks – TryHackMe

**Room type:** Walkthrough • **Difficulty:** Easy • **Tasks:** 8  
**Goal:** Understand and exploit client-side (DOM) vulnerabilities by tracing data flow from untrusted sources to dangerous sinks.

---

## What I Practiced
- Mapping **source → sink** flows in the browser: `location.search`, `location.hash`, `document.cookie`, `localStorage`, `postMessage` → `innerHTML`, `document.write`, `eval`, `setTimeout(String)`, event handler attributes.
- Using **DevTools** (Sources, Console, DOM/XHR/Mutation breakpoints) to trace tainted data and confirm execution paths.
- Crafting and weaponizing **DOM XSS** payloads and bypasses; validating impact (alert, cookie read, action hijack).
- Reviewing **frontend framework** nuances (Vue/React/Angular) where unsafe render APIs (`v-html`, `dangerouslySetInnerHTML`, client-side templating) can reintroduce risk.

---

## Quick Reference

**Common Sources**
- `location.search`, `location.hash`, `document.referrer`
- `document.cookie`, `localStorage/sessionStorage`
- `window.name`, `postMessage` data, XHR/fetch responses (when trusted blindly)

**Dangerous Sinks**
- `element.innerHTML`, `outerHTML`, `insertAdjacentHTML`
- `document.write`, `Range.createContextualFragment`
- `eval`, `new Function`, `setTimeout("...")`, `setInterval("...")`
- Inline/event-handler attributes (e.g., `onclick`)

**Useful Test Payloads**
```html
<img src=x onerror=alert(1)>
<svg onload=alert(1)>
" onmouseover=alert(1) x="
javascript:alert(1)
