# Delivery Date Confidence Calculator

**Turn three-point estimates into a delivery date you can actually defend.**

A single HTML file. Open it in a browser and it works — no install, no build, no account, no network. Save the page to your laptop and it still runs on a plane.

---

## The problem it solves

The default way teams set a date is to collect everyone's "likely" estimate and add them up. That plan only holds if nothing runs long. Because delays compound and parallel work waits on its slowest branch, the summed-likely date typically carries a **20–40% chance of being met** — and this tool tells you the exact number for *your* plan.

That figure is usually the most uncomfortable and most useful output on the page.

## What it gives you

| Output | What it's for |
|---|---|
| **P50 / P80 / P90 finish dates** | P80 is the defensible commit — four runs in five landed on or before it |
| **Confidence in your committed date** | Enter the date you already promised; get the honest probability |
| **Days needed to reach 80%** | The size of the ask, in days, when you have to renegotiate |
| **Risk driver ranking** | Which task's uncertainty is actually deciding your date |
| **Naive-plan confidence** | What the summed-likely date is really worth |
| **Distribution + S-curve charts** | For the slide where someone asks "how confident are you?" |
| **Markdown summary** | One click, pastes into a status doc or ticket |

## How to use it

1. **Open `index.html`** in any browser. An example plan is loaded so you can see the shape of it immediately.
2. **Enter your tasks** with three estimates each, in days:
   - **Best case** — genuinely unobstructed, not sandbagged
   - **Likely** — what you'd actually bet on
   - **Worst case** — a bad-but-real week, not a catastrophe
3. **Group with phases.** Tasks sharing a phase name run **in parallel** (the phase takes as long as its slowest task). Phases run **sequentially**. Give every task its own phase name for a purely serial plan.
4. **Set the start date**, pick working days or calendar days, and optionally enter the date you've already committed to.
5. **Run simulation.** Read the P80 row, then read the risk drivers.

CSV import/export uses the column order `Phase, Task, Optimistic, Likely, Pessimistic` — a header row is optional, so a quick export from Jira or a spreadsheet drops straight in.

## Reading the output

**The P50 → P80 gap is the risk you're carrying.** A narrow gap means the plan is robust. A wide gap means your date depends on how a few uncertain tasks happen to land, and no amount of confident language in a status report changes that. Hold the gap as *visible program buffer* rather than letting each estimator pad their own number — padding hidden inside tasks gets consumed silently; buffer held at the program level gets managed.

**The risk driver ranking is where your effort pays.** It correlates each task's sampled duration against the total across every run. The top one or two are the tasks worth splitting, spiking, de-risking, or re-estimating. Anything scoring near zero — including a small task sitting in a parallel phase behind a much longer sibling — is **not on your risk path**, and shortening it buys you nothing. That result surprises people, and it's usually the most actionable thing on the page.

**Rule of thumb on estimates:** if a task's worst case is more than roughly 3× its best case, the task is too big to estimate. Split it.

## The math

Each simulation run draws a duration for every task from its three-point estimate, takes the longest task in each phase, and sums the phases. Twenty thousand runs (default) build the distribution.

- **PERT** — a beta distribution fitted so the mean is `(o + 4m + p) / 6`, weighting the likely case four times as heavily as the extremes. The standard project-estimating choice. Variance is `(μ−o)(p−μ)/7`.
- **Triangular** — probability spread more evenly, mean `(o + m + p) / 3`. The safer pick when your "likely" figure is really a guess.

Beta samples come from a Marsaglia–Tsang gamma sampler; triangular uses inverse-CDF. Both samplers are verified against their analytic means and standard deviations, and the phase, percentile and working-day date arithmetic are covered by round-trip checks.

## Limits worth stating out loud

- **Task durations are drawn independently.** A shared root cause — one vendor, one key engineer out, one flaky environment — that hits several tasks at once is not modelled. In that situation treat the P80 as a floor.
- **Scope change and unknown work aren't modelled.** Nothing simulates the work you haven't thought of yet.
- **Dependencies are limited to the phase grouping.** Arbitrary cross-phase dependency chains need a real scheduling tool.
- **Garbage in, garbage out.** Three-point estimates from people guessing under pressure produce confident-looking nonsense. The tool makes uncertainty visible; it doesn't manufacture information.

## Privacy

Everything runs locally in your browser. There is no network request, no analytics, no external script or stylesheet, and no data ever leaves the page. Your task list is kept in that browser's local storage only — **Clear all** removes it. Verify it yourself: the file contains zero `http` references.

## License

MIT. Use it, fork it, rebrand it, put it on your team's intranet.
