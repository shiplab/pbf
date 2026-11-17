# Measuring the cost of uniqueness — interactive model

Live page: **https://shiplab.github.io/pbf/**

Repository: https://github.com/shiplab/pbf

This is the interactive companion of the paper

> Yilmaz, G., Gaspar, H.M. *Measuring the cost of uniqueness: shipbuilding learning evidence applied to project-based firms.* Preprint, NTNU Ålesund, 2026.

The page follows the paper step by step. The worked example of Section 2 (core cost 100,000 labour hours), the detailed case of Firm X (Section 3) and the tool and AI-assistant scenario (Section 5.2) are reproduced with the base values; a firm can enter its own values. The simulation experiments of Section 4 are not part of the page.

## The model

The model starts from Erichsen's learning effect for ship series, adds a floor at the core cost and a novelty penalty, and then one factor at a time. Each factor moves the experience stock `E` with its own shape.

```
y_n = a · n^b,   b = log2(1 − S)                      Erichsen's learning effect (2.1)
h(E) = B · (1 + u(E)),   u(E) = max[0, (λ + f)(1 + E)^b − λ]   floor and novelty penalty (2.2)
E ← E + ρ                                             similar project completed: step up (2.3)
E ← max(0, E − m · max(0, g − g0))                    time without related work: slow fade (2.4)
E ← E · d^τ                                           unrelated project of τ months: fast fall (2.5)
E ← E · (1 − q)                                       people and partners leaving: drop (2.6)
f ← (1 − φ) · f,   E_available = E + e_max · min(1, t/T)   reuse; digital tool as a ramp (2.7)
C = B · (1 + u) · (1 + c(u)),   c(u) = c_r + (c_1 − c_r) · min(1, u/f)   customer changes (2.8)
```

- `B` core cost, `f` novelty penalty, `S` learning rate per doubling, `ρ` similarity of an earlier project to the new one.
- `λ` is the strength of the learning effect (2.9): 1 is the base case, in which experience lowers the whole cost of a new design as in a ship series; 0 is the weak case, in which it reduces only the novelty penalty.
- Base values: `S` = 5.7% (`b` = −0.0846, Erichsen 1994), `f` = 10% (Craggs et al. 2004), `d` = 0.75 a month (Argote et al. 1990), `c_1` = 12.3% and `c_r` = 3.0% (Coleman et al. 2007); `m` = 0.05, `g0` = 6 months, `e_max` = 1 and `T` = 24 months are assumptions.
- The visible cost of uniqueness is what a project costs above a repeat. The hidden cost is what the following projects cost more because experience was lost.

## The page

Open `index.html`. No server or build step; the page is one file (fonts are loaded from Google Fonts when online). Every input is a control and every plate recalculates at once.

| Plate | Content | Paper |
|---|---|---|
| Estimate | Cost of the project for the scenario of the controls, with the weak case and the steps that lead to the experience available | Sections 2.1–2.9 |
| Step 2.1 | Erichsen's learning curve | Fig. 1 |
| Step 2.2 | Floor at the core cost and novelty penalty | Fig. 2 |
| Step 2.3 | Experience from similar projects | Fig. 3 |
| Steps 2.4–2.6 | Three losses: time without related work, an unrelated project, people leaving | Fig. 4 |
| Step 2.7 | Reuse and digital tools | Fig. 5 |
| Step 2.8 | Customer changes; visible and hidden cost | Fig. 6 |
| Step 2.9 | Strength of the learning effect | Section 2.9; weak-case marks of Fig. 7 |
| Section 3 | Firm X: history, experience stock, bid, an unrelated project offered, narrowing the estimate | Figs. 8–11 |
| Section 5.2 | Levers for a firm with no related experience; the AI assistant as a scenario | Fig. 14 |
| Table 1 | Factors, shapes, base values and the status of each source | Table 1 |

## Reproducing the paper's numbers

With the base values, the buttons under "Situations from the paper" give:

- design new to the firm: 123,500 labour hours; a repeat: 103,000;
- after two and after five similar projects (similarity 0.6): 108,800 and 103,000;
- after five, then 36 months without related work: 106,500;
- after five, then a 12-month unrelated project: 121,700 (hidden cost on the following projects 35,300, Step 2.8);
- after five, then half of the experience leaves: 106,500;
- new design with an earlier design reused: 113,000; with the tool fully in use: 110,500;
- Firm X: bid 108,500 at the judged stock (1.23) and 113,400 at the measured stock (0.70).

## Files

- `index.html` — the whole application (markup, styles and script in one file).
- `LICENSE` — MIT.

## Authors

Gokce Yilmaz and Henrique M. Gaspar, Department of Ocean Operations and Civil Engineering (IHB), NTNU Ålesund. Developed with the assistance of Claude (Anthropic).

## Citing

If you use the model or the page, cite the paper above and this repository (version tag and date).

## License

MIT, see `LICENSE`.
