# Spec Generator

A tiny, dependency-free tool that turns a blank page into a usable spec — the
kind you'd hand to an AI coding agent (Claude, Copilot, Cursor, whatever)
before asking it to generate anything.

## Why

AI coding agents have gotten fast enough that writing code is rarely the
bottleneck anymore. The bottleneck moved upstream: precisely defining what
"done" means. A spec that only covers the happy path leaves the agent to
guess at constraints, failure handling, and scope — and it will guess wrong
often enough to matter.

This tool prompts for the six things that consistently make the difference:

1. **Goal** — the observable outcome
2. **Inputs / Outputs** — concrete types and shapes, not vague nouns
3. **Constraints** — performance, persistence, security, compliance
4. **Failure modes** — what happens when a dependency fails
5. **Out of scope** — what the agent should *not* build
6. **Acceptance criteria** — how you'll verify it's actually done

Fill in what you know, copy or download the generated Markdown, and drop it
straight into your prompt, PR description, or ticket.

## Usage

No install, no build step. Either:

- Open `index.html` directly in a browser, or
- Serve this folder with GitHub Pages / any static host

Everything runs client-side; nothing is saved or sent anywhere.

## License

MIT — use it, fork it, adapt it for your team.
