# The cost of uniqueness — interactive model

A single-file interactive version of a cost model for unique complex projects in project-based firms (PBFs) delivering complex products and systems, adapted from shipbuilding learning evidence.

Open `index.html` in any browser. No server, build step or dependencies; it works offline.

## What the page does

- **Scenario controls** for every input: core cost and unit, novelty premium, change orders, learning rate, past projects and their relatedness, gap and forgetting, plus λ (the share of core work a new design makes learnable again: 0 = Form A, only the premium is learnable; 1 = Form B, whole design cost to the floor) and the published forgetting rates.
- **Plate 0** — the model: `C = B(1 + c) + U`, `U = B·u(n)·(1 + c)`, `u(n) = max[0, (λ + f)(1 + n)^b − λ]`, with the status of each input (sourced, adapted, assumed).
- **Plate 1** — the estimate for the scenario, built up step by step.
- **Plate 2** — the same project bid by two firms, and three levers for the less experienced one (reuse, frozen specification, knowledge tools).
- **Plate 2b** — a project-history table (relatedness judged and measured, gaps) that draws the experience stock, gives the bid interval before and after a digital thread, and the next-year decision (related, unrelated or no project) at the judged and measured stock.
- **Plates 3–4** — a series versus a run of unique projects, and what a gap costs.
- **Plate 4b** — interrupting a series with an odd contract (Erichsen's observation): the hidden cost on the ships that follow, against the contract's visible uniqueness cost, for a chosen duration and retention rate.
- **Plate 5** — more views (relatedness, heat map, tornado).
- **Plate 6** — investment in knowledge tools: learning, reuse and core-productivity channels.
- **Plates 7–8** — sources and how far to trust them; hypotheses and what would settle them.

Base case: 122,071 labour hours in Form A for a 100,000-hour core (novelty 10%, change orders 12.3%, learning 6.5% per doubling, six related projects at relatedness 0.6, 14 months since the last).

## Authors

Gokce Yilmaz and Henrique M. Gaspar, Department of Ocean Operations and Civil Engineering, NTNU Ålesund. Developed with the assistance of Claude (Anthropic); reviewed and edited by the authors.

## License

MIT, see `LICENSE`.
