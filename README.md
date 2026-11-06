# Measuring the cost of uniqueness — interactive model

Live page: **https://shiplab.github.io/pbf/**

Repository: https://github.com/shiplab/pbf

This is the interactive companion of the paper

> Yilmaz, G., Gaspar, H.M. *Measuring the cost of uniqueness: shipbuilding learning evidence applied to project-based firms.* Preprint, NTNU Ålesund, 2026.

Every number in the paper's tables and figures can be reproduced on the page, and a firm can enter its own values.

## What the model does

A unique project costs the repeat cost of the same work plus the cost of uniqueness. The cost of uniqueness has a visible part — the novelty premium and the change orders of the project itself — and a hidden part, the experience the project takes from the line of work the firm is on (Erichsen's observation that an odd contract in a series of ships sends the next ship almost back to first-ship cost).

```
C = B(1 + c) + U,   U = B · u(n) · (1 + c)
u(n) = max[0, (λ + f)(1 + n)^b − λ],   b = log2(1 − S)
E(k+1) = max(0, E(k) + ρ(k) − m · max(0, g(k) − g0))      gap between related projects
E(k+1) = E(k) · d^τ + ρ(Z),  ρ(Z) ≈ 0                      unrelated contract of τ months
```

- `B` core cost, `f` novelty premium, `c` change orders, `S` learning per doubling, `n` effective experience.
- `λ` is the share of core work a new design makes learnable again: 0 = Form A (only the premium is learnable), 1 = Form B (the whole design cost follows the curve to the floor).
- `m`, `g0` idle forgetting; `d` monthly retention while an unrelated contract runs (0.75 from Argote et al., 1990, reproduces Erichsen).

## The page

Open `index.html`. No server, build step or dependencies; it works offline. Every input is a control; every plate updates at once.

| Plate | Content | Paper |
|---|---|---|
| 0 | The model and the status of each input (sourced, adapted, assumed) | Section 2, Table 1 |
| 1 | The estimate for the scenario, built up step by step | Section 3 |
| 2 | Two firms bid the same project; three levers for the less experienced one | Section 3, Table 2, Fig. 2 |
| 2b | Project history with relatedness judged and measured; experience stock; bid interval before and after a digital thread; the next-year decision (related, unrelated or no project) with its hidden cost | Section 4, Tables 3–5, Fig. 4; Section 5, Fig. 5 |
| 3 | A series versus a run of unique projects; Erichsen's series model | Section 2, Fig. 1 |
| 4 | What a gap between projects costs | Section 6 |
| 4b | A custom project interrupting a line of repeat projects: visible cost, hidden cost on the projects that follow, how far the next project returns toward first-project cost | Section 3, Fig. 3; Section 6, Table 6 |
| 5 | More views: curve family, relatedness, heat map, tornado | Section 6, Fig. 7 |
| 6 | Investment in knowledge tools: learning, reuse and core-productivity channels | Section 5, Eq. (5) |
| 7–8 | Sources and how far to trust them; hypotheses and what would settle them | Sections 6–7 |

Base case: 122,071 labour hours in Form A for a 100,000-hour core (novelty 10%, change orders 12.3%, learning 6.5% per doubling, six related projects at relatedness 0.6, 14 months since the last); 112,300 in Form B.

## Reproducing the paper's numbers

- Mock-up case (Table 2): default scenario; switch λ between 0 and 100% for the two forms.
- Custom project in a line (Fig. 3, Table 2 rows): Plate 4b with λ = 100%, six projects, interruption after the fourth, 12 months, retention 75%.
- Detailed case (Tables 3–5, Fig. 4): Plate 2b, "reset to the paper's detailed case".
- Change orders falling with experience (Section 6): the checkbox under the change-order slider.

## Files

- `index.html` — the whole application (markup, styles and script in one file).
- `LICENSE` — MIT.

## Authors

Gokce Yilmaz and Henrique M. Gaspar, Department of Ocean Operations and Civil Engineering (IHB), NTNU Ålesund. Developed with the assistance of Claude (Anthropic); reviewed and edited by the authors.

## Citing

If you use the model or the page, cite the paper above and this repository (version tag and date).

## License

MIT, see `LICENSE`.
