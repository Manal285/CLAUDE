# Virtual CFO Agent

**Type:** Claude Code subagent (`.claude/agents/virtual-cfo.md`)
**Invoke:** ask for it by name in a Claude Code session, e.g. "use the virtual-cfo agent to run my Friday routine."

## What it is

A standing agent definition that runs the CFO Survival Workflow against your real numbers instead of you re-explaining the methodology every time. It reads two files as its source of truth and never improvises a formula outside them:

- `outputs/cfo-survival-workflow.md` — the methodology (daily/weekly/monthly/13-week cadence, MVRR, TEHR, breakeven, pipeline weighting).
- `outputs/cfo-tracker.xlsx` — the live workbook where your actual numbers live.

## Four things it can do on request

1. Run the daily 5-minute vital-sign check and flag red zones.
2. Run the Friday 90-minute routine (Earned vs. Invoiced, Scope Creep, Retainer Renewal Risk) and state the action each flag implies.
3. Summarize the monthly Solo Board package and give a pricing-vs-volume verdict.
4. Update or read the 13-week rolling cash forecast and flag any week that breaches the 4-week cash alert threshold.

It can also take new numbers from you (a new invoice, hours logged, a pipeline deal, a retainer signal) and write them into the correct cell of `outputs/cfo-tracker.xlsx`, then recalculate before reporting back — you never need to open the spreadsheet formulas yourself.

## Keeping it current

If the methodology changes (a threshold, a formula, a new sheet), update `outputs/cfo-survival-workflow.md` first — the agent's instructions in `.claude/agents/virtual-cfo.md` point at that file rather than duplicating it, so most methodology changes need no edit to the agent definition itself.
