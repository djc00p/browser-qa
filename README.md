# 🛡️ Browser QA

[![ClawHub Skill](https://img.shields.io/badge/ClawHub-Skill-blue)](https://clawhub.ai/djc00p/browser-qa) [![Agent Skill](https://img.shields.io/badge/Agent-Skill-blue)](#) [![Accessibility](https://img.shields.io/badge/WCAG-AA-4285F4.svg)](https://www.w3.org/WAI/standards-guidelines/wcag/) [![Web Vitals](https://img.shields.io/badge/Web-Vitals-0F9D58.svg)](https://web.dev/vitals) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Browser QA** is a structured four-phase methodology for verifying UI behavior, visual consistency, and accessibility.

The phases run in order for a reason: smoke test first catches hard breakage before interaction testing wastes time on it, and visual regression before accessibility catches layout problems that would otherwise be misreported as a11y failures.

---

## ⚠️ Before You Run: Scope and Safety

This skill drives a real browser and can submit forms, log in, and complete checkouts. **Those actions change state on the target site.**

**Use it only against sites you own or have written permission to test.** Before the first interaction, confirm with the user:

* **Target URL** — a staging, sandbox, or test environment. **Not production.**
* **Test credentials** — a dedicated test account, never a personal or admin account
* **Test payment data** — a sandbox/test card, never a real card
* **What may be submitted** — which forms, which flows, and whether checkout may complete end-to-end

> **Never** submit a form, create an account, log in with real credentials, or complete a checkout on production unless the user explicitly approves that exact action. Do not treat *"run the QA suite"* as approval for state-changing steps. If a flow is ambiguous, ask.

Prefer read-only checks first: navigate, assert on visible content, screenshot. Only submit when the specific submission has been approved.

---

## 🚀 Quick Start

1. **Phase 1: Smoke Test** — navigate, check console errors, verify Core Web Vitals
2. **Phase 2: Interaction Test** — click links, submit forms, verify user flows
3. **Phase 3: Visual Regression** — screenshot key pages at 3 breakpoints
4. **Phase 4: Accessibility** — run axe-core, verify keyboard nav, check landmarks

---

## 🔍 The Four Phases

### Phase 1 — Smoke Test

```text
1. Navigate to target URL
2. Check for console errors (filter analytics noise)
3. Verify no 4xx/5xx in network requests
4. Screenshot above-the-fold (desktop + mobile)
5. Check Core Web Vitals: LCP < 2.5s, CLS < 0.1, INP < 200ms
```

### Phase 2 — Interaction Test

```text
1. Click every nav link — verify no dead links
2. Submit forms with valid data — verify success state
3. Submit forms with invalid data — verify error state
4. Test auth flow: login → protected page → logout
5. Test critical journeys: checkout, onboarding, search
```

### Phase 3 — Visual Regression

```text
1. Screenshot key pages at 3 breakpoints (375px, 768px, 1440px)
2. Compare against baseline screenshots (if stored)
3. Flag layout shifts > 5px, missing elements, overflow
4. Check dark mode if applicable
```

### Phase 4 — Accessibility

```text
1. Run axe-core on each page
2. Flag WCAG AA violations (contrast, labels, focus order)
3. Verify keyboard navigation works end-to-end
4. Check screen reader landmarks
```

---

## 🛠 Automation Tools

| Tool | Setup | Speed | Multi-Browser | Screenshots |
|------|-------|-------|---------------|-------------|
| **claude-in-chrome** | Easy (existing Chrome) | Fast | No | Excellent |
| **Playwright** | Medium | Slow | Yes | Good |
| **Puppeteer** | Easy | Fast | No | Good |

* **claude-in-chrome** — real user conditions, native performance
* **Playwright** — cross-browser coverage when you need it
* **Puppeteer** — quick smoke tests and screenshots

---

## 📋 Output Format

```text
## QA Report — [URL] — [timestamp]

### Smoke Test
- Console errors: 0 critical, 2 warnings (analytics noise)
- Network: all 200/304, no failures
- Core Web Vitals: LCP 1.2s ✓, CLS 0.02 ✓, INP 89ms ✓

### Interactions
- [✓] Nav links: 12/12 working
- [✗] Contact form: missing error state for invalid email
- [✓] Auth flow: login/logout working

### Visual
- [✗] Hero section overflows on 375px viewport
- [✓] Dark mode: all pages consistent

### Accessibility
- 2 AA violations: missing alt text, low contrast footer links

### Verdict: SHIP WITH FIXES (2 issues, 0 blockers)
```

---

## 📚 References

* `references/tools.md` — browser automation tooling (claude-in-chrome, Playwright, Puppeteer) with examples
* `references/wcag.md` — WCAG AA checklist and common violations

---

**Adapted from [everything-claude-code](https://github.com/affanm/everything-claude-code) by [@affaan-m](https://github.com/affaan-m) (MIT).**

**Published by [@djc00p](https://github.com/djc00p)**
