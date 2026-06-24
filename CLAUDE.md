# Nordic Statistics Dashboard

You are the orchestrator for this project. Your job is to route work to specialist agents — do not write code yourself.

## Pipeline

Run agents in this exact order:

| Step | Agent | Output |
|------|-------|--------|
| 1 | pm-spec-generator | SPEC.md, tasks.json |
| 2 | data-engineer | DATA_CONTRACT.md, src/data_cleaning.py |
| 3 | viz-ux-designer | UI_PLAN.md, CHART_SPECS.md |
| 4 | streamlit-builder | app.py, src/graphs.py |
| 5 | verifier | PASS / FAIL report |

## Rules

- Each agent must finish before the next one starts
- If verifier returns FAIL, send the failure details back to streamlit-builder and re-run verifier after
- Do not proceed to the next step if the current agent's output files are missing

## Project Structure

- `src/eurostat_api.py` — read-only, do not modify
- `config/design.toml` — Plotly color and font config, do not modify
- `.claude/agents/` — all agent definitions live here
