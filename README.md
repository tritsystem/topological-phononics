# Topological phononic reservoir

[![DOI](https://zenodo.org/badge/1297052917.svg)](https://doi.org/10.5281/zenodo.21305151)

**When does topological structure make an analog reservoir tolerate a dead element — and when doesn't it?**

A pre-registered simulation study of the SSH resonator chain used as a physical reservoir, taken down the full scoping ladder until the claim stopped giving. Conducted under the [tritsystem method](tritsystem-method.pdf): pre-register the test, validate the instrument, split the average, find the boundary, and write the "no" as carefully as the "yes."

## The result, in one sentence

Topological structure protects a reservoir's computation against a dead element **exactly when chiral symmetry holds** — several-fold in the idealized model, weaker under nonlinearity and noise, beaten by generic redundancy, and only marginally (statistically inconclusive) in a realistic damped/nonlinear device. **The idealized magnitude does not transfer to hardware; the chiral boundary condition does.**

**Preprint:** [preprint.pdf](preprint.pdf) (source: [PREPRINT.md](PREPRINT.md)) — the formal write-up, ready for Zenodo. Extended lab report with every number and the honest ledger of what did *not* hold: **[LAB_REPORT.md](LAB_REPORT.md)**.

## Engineering practices, not just physics

This is simulation research, but it's held to a software-engineering standard, not just a scientific one:

- **Every claim ships with a self-test.** `python phononic_methods.py` reproduces the paper's own reported numbers from the actual code path — not a separate "trust me" writeup. If the numbers ever drift, the test catches it.
- **Pre-registered, not post-hoc.** Each experiment script states its prediction before running, so a result can't be quietly reframed as a win after the fact — including when a pre-registered prediction was wrong (§8 in the lab report is a named retraction, kept in, not deleted).
- **One command regenerates every figure.** `python animate.py` rebuilds all three GIFs directly from the live method, so the demos can never silently drift out of sync with the code.
- **The paper itself is built by a script** (`build_preprint.py`) — the PDF is a compiled artifact of the repo, not a hand-maintained document that can fall out of sync with the code.
- **Negative and null results are reported with the same rigor as positive ones** — several sections of the lab report are "this hypothesis did not survive testing," stated as plainly as the sections that did.

## Demos — every frame computed live from the real method

**The topological edge mode forming as the dimerization sweeps trivial → topological:**

![edge mode forming](edge_transition.gif)

**A dead resonator swept along the chain — topological degrades more gracefully (linear task, idealized model):**

![defect sweep](defect_sweep.gif)

**Noise as a feature — the trained readout cancels structured noise; only the full-rank thermal floor survives:**

![noise sweep](noise_sweep.gif)

## Run it

No dependencies beyond `numpy` + `matplotlib`.

```bash
python phononic_methods.py   # self-test: reproduces the reported numbers (the fidelity check)
python dashboard.py          # interactive: sliders over edge mode / defect / noise, live
python animate.py            # regenerate the three GIFs above
```

## What's here

- **[LAB_REPORT.md](LAB_REPORT.md)** — the honest, fully-scoped write-up + ledger. This is the real evidence trail; everything below feeds into it.
- `phononic_methods.py` — the core methods, verbatim, with the self-test that reproduces the paper numbers.
- `dashboard.py`, `animate.py` — interactive + shareable demos on top of the verified methods.
- `build_preprint.py` — compiles [PREPRINT.md](PREPRINT.md) into `preprint.pdf`.

**~20 pre-registered experiment scripts, grouped by what they test** (each is independently runnable; see the report's reproducibility list for exact figures/claims tied to each):

| Group | Scripts | Question |
|---|---|---|
| Foundations | `reservoir_from_scratch.py` | A reservoir built from nothing but `numpy`, every design choice explained inline — the "if this doesn't work, nothing above it will" baseline. Start here if you want to see the underlying idea with no topology/physics layered on yet. |
| Edge mode & chiral protection | `ssh_topological_reservoir.py`, `phase_transition_defect.py`, `cross_device_transfer.py`, `cross_device_transfer_tight.py` | Does the topological edge mode form, and does protection track the chiral-symmetry invariant specifically? |
| Defect tolerance & scaling | `ssh_defect_position.py`, `ssh_multiple_defects.py`, `ssh_scaling.py` | Where does the advantage hold, and does it survive from 8 to 64 nodes? |
| Noise & the high-Q crossover | `reservoir_cavity_noise.py`, `reservoir_cavity_v2.py` | Does cavity quality trade raw memory for noise-robustness? |
| Noise as a feature (readout subspace) | `noise_feature.py`, `noise_feature_stage.py`, `rank_margin.py`, `rank_margin_aware.py`, `scaling_margin.py`, `combined.py` | Can a trained linear readout cancel *structured* noise while a full-rank noise floor survives untouched? |
| Nonlinear task & architecture control | `narma_test.py`, `narma_redundancy.py` | Does the effect hold on a genuinely nonlinear benchmark (NARMA10), and does it survive a redundancy control (matched-density random network)? |
| Physical device model | `duffing_device.py`, `firm_chiral.py`, `circuit_predict.py`, `measure_and_train.py` | Replacing the idealized tight-binding model with real damped/driven nonlinear (Duffing) oscillator dynamics, plus a real hardware acquisition pipeline (`--sim` today, `--hw` reads real ADC voltages) — does the effect survive contact with something closer to hardware? |
| Quasicrystal/Fibonacci connectivity (separate sub-thread) | `fibonacci_connectivity.py` and the other `fibonacci_*.py` scripts, `debruijn_quasicrystal_reservoir.py` | Can a 3-parameter recursive generation rule replace an O(N²)-stored random connectivity matrix without losing capability? |
| Real hardware/audio transfer | `real_audio_reservoir_test.py`, `rkky_magnetic_reservoir.py` | Does the finding transfer to a real recorded audio signal / a different physical substrate (magnetic RKKY coupling)? |

## Scope (read before citing)

Simulation only (tight-binding + a damped/driven Duffing ODE model); linear-memory and NARMA10 reservoir tasks. This is a **candidate primitive characterized honestly**, not a fabricated device — and **not** a quantum computer. A hardware build would need deliberate chiral-symmetry engineering merely to avoid a *reversal* of the effect, and should expect a modest advantage, not the idealized ~5×.

## Cite

If you use this work, please cite it via its DOI (see also `CITATION.cff` — GitHub's "Cite this repository" button):

> tritsystem (2026). *Topological protection as a defect-tolerant reservoir primitive: a pre-registered simulation study of when it holds.* Zenodo. https://doi.org/10.5281/zenodo.21305151

## Related

- [methodlm](https://github.com/tritsystem/methodlm) — the honest-measurement / causal-reasoning harness.
- The operating discipline this study followed: [tritsystem-method.pdf](tritsystem-method.pdf).
