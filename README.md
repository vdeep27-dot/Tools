# Tools

Public tools that ease life — small, free utilities for project managers, program managers and product leads. A new one lands most weeks.

Every tool here follows the same rules:

- **One HTML file.** Open it in a browser. Nothing to install, build, sign up for or configure.
- **Runs fully offline.** No network requests, no analytics, no external scripts, no trackers. Save the page and it still works.
- **Your data stays yours.** Nothing is uploaded. Anything a tool remembers lives in your own browser's local storage.
- **MIT licensed.** Fork it, rebrand it, put it on your intranet.

---

## Tools

| Added | Tool | What it does |
|---|---|---|
| 2026-W39 | [Delivery Date Confidence Calculator](public/delivery-date-confidence/) | Monte Carlo schedule simulator. Turns three-point estimates into P50/P80/P90 delivery dates, tells you the real probability of hitting a date you've already committed to, and ranks which task is actually driving your risk. |
| 2026-W39 | [Spec Generator](public/spec-generator/) | Prompts you for the six things an AI coding agent can't guess — goal, I/O, constraints, failure modes, out of scope, acceptance criteria — and hands back clean Markdown to paste into a prompt, PR or ticket. |

---

## Using them

Two options:

1. **Download** — grab the tool's `index.html` and double-click it. That's the whole install.
2. **Serve it** — the `public/` folder is a static site. Point GitHub Pages at it, or drop it on any web server or shared drive.

No build step exists because there's nothing to build.

## Contributing

Issues and PRs welcome — especially corrections to the math, accessibility fixes, and reports of a tool behaving badly in a browser you have to use.

If you're adding a tool, it has to meet the four rules above. A dependency-free single file is the constraint that makes these things survive: no supply chain, no CDN that disappears, no version drift, and any PM can read the source and satisfy their security team in an afternoon.

## License

[MIT](LICENSE)
