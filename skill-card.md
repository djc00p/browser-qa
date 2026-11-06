## Description:

Automate visual testing and UI interaction verification with a four-phase methodology covering smoke tests, interaction tests, visual regression, and WCAG AA accessibility audits.

This skill is ready for commercial/non-commercial use.

## Publisher:

[djc00p](https://clawhub.ai/user/djc00p)

### License/Terms of Use:

MIT-0

## Use Case:

Developers and QA engineers use this skill to run structured browser checks before release, including console and network smoke tests, forms and auth flows, responsive screenshots, and accessibility checks.

### Deployment Geography for Use:

Global

## Known Risks and Mitigations:

Risk: Browser interaction testing can submit forms, create accounts, or exercise checkout flows on live sites.

Mitigation: Use staging or sandbox URLs, test accounts, and test payment data; require explicit approval before submitting forms, creating accounts, or completing checkout on production.

Risk: Automated accessibility scans can miss keyboard, screen reader, zoom, and semantic HTML issues.

Mitigation: Pair axe-core or similar automated checks with manual keyboard navigation, screen reader landmark checks, and 200% zoom review.

Risk: Browser automation results depend on the chosen runtime and available local browser support.

Mitigation: Select the browser tool that matches the target coverage, and document any dependency such as Chrome, Playwright, or Puppeteer before relying on results.

## Reference(s):

- [Browser QA - Automation Tools](references/tools.md)
- [WCAG AA Accessibility Checklist](references/wcag.md)

## Skill Output:

**Output Type(s):** [text, markdown, code, shell commands, guidance]

**Output Format:** [Markdown QA report with optional code and shell command snippets]

**Output Parameters:** [1D]

**Other Properties Related to Output:** [May include screenshot and test artifact guidance when browser automation is used.]

## Skill Version(s):

1.0.1 (source: release evidence)

## Ethical Considerations:

Users should evaluate whether this skill is appropriate for their environment, review any generated or modified files before relying on them, and apply their organization's safety, security, and compliance requirements before deployment.
