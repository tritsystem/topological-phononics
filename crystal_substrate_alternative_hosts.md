# Scoping alternative point-defect qubit hosts beyond diamond NV centers

**tritsystem** (independent researcher), 2026-08-21
Companion follow-up to `crystal_substrate_scoping_nv_ferroelectric.md`, which found diamond NV centers are real and well-documented but have no published "defect spacing vs. inter-channel crosstalk" curve — only a density-vs-bath-decoherence relationship, a different physical axis than the spacing-vs-crosstalk curves already measured for the photonic (Pr:YSO spectral hole burning, monotonic/saturating BER-vs-spacing) and phononic (SSH topological reservoir, non-monotonic/humped defect-penalty-vs-dimerization) substrates in this project. **This is a literature scoping pass, not new simulation or measurement.** Same discipline as before: real citable sources, explicit confirmed/uncertain flags, honest gaps.

**Bottom line up front:** three real alternative point-defect-qubit hosts were found and are worth tracking — SiC divacancy/silicon-vacancy centers, silicon T/G centers, and hBN spin defects. None has a published curve that is a clean, direct analog of "spacing between two individually-addressed defects vs. crosstalk error rate between them." All three *do* have a real density-vs-decoherence relationship (the same axis diamond has), and all of those are **monotonic** (power-law or quadratic, never humped). The single closest analog to a genuine spacing-vs-crosstalk curve — a 2024 hBN donor-acceptor coupled-pair study — has a **threshold/critical-window shape** (unusable at sub-2 nm separation, converging smoothly to isolated-defect behavior beyond it), which is neither the photonic nor the phononic shape and is flagged as potentially a third category. **No genuine topological or phase-transition connection was found for any of these hosts** — every "topological" hit returned by search was about unrelated photonic-crystal band topology, not point-defect spin qubits. This absence is itself a real finding, consistent with the working hypothesis that simple two-level/multi-level spin-optical defects produce monotonic crosstalk behavior by construction, lacking the protected-mode structure that produces the phononic system's hump.

---

## 1. Silicon carbide (SiC): divacancy (VV) and silicon-vacancy (VSi) centers

### Why it's real and credible
SiC divacancy and silicon-vacancy spin defects are an actively researched, well-established NV-alternative platform, notable specifically for being CMOS-compatible (industrial-scale single-crystal growth, established doping and nanofabrication, unlike diamond). Room-temperature coherent single-spin control with 30% readout contrast and 150 kcps photon count rate has been reported, and coherence times up to 64 ms have been reported for the neutral divacancy. ([PMC9160373](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9160373/), [OSTI review](https://www.osti.gov/pages/servlets/purl/1339658))

### Density/concentration vs. relaxation: a real, quantitative, monotonic curve
Bulancea Lindvall, Son, Abrikosov & Ivády, *"Dipolar spin relaxation of divacancy qubits in silicon carbide,"* npj Computational Materials 7, 213 (2021), arXiv:2102.01782, gives an explicit analytical relationship between point-defect spin concentration C and the zero-field relaxation rate:

**T₁⁻¹(B=0, C) = βC², with β = 1.6×10⁻³⁵ Hz·cm⁶**

The paper explicitly notes this **quadratic** dependence differs from earlier experimental reports that had assumed a *linear* concentration dependence — a real, citable correction to prior assumptions in the field. A broader field-dependent fit uses a form X(C) = α + βCⁿ with fitted exponents n ranging 0.875–2.0 depending on the parameter. Separately, T₁ exhibits **resonant drops of several orders of magnitude at specific magnetic fields** (ground-state level anti-crossing, B_GSLAC ≈ 480 G and B_GSLAC/2 ≈ 240 G) via nuclear/electron spin flip-flops — but this is a magnetic-field-axis effect, orthogonal to the concentration dependence, not a spacing/crosstalk effect. ([arXiv:2102.01782 / npj Comp Mater](https://www.nature.com/articles/s41524-021-00673-8))

**Honest read:** this is the same physical axis as the diamond NV case (dopant/defect density → dipolar-bath-induced decoherence), not inter-channel readout crosstalk between two individually addressed qubits. It is, however, a cleaner and more explicit quantitative result than what was found for diamond — an actual fitted power law (quadratic, corrected from an assumed-linear prior belief) rather than a qualitative density-vs-coherence-time table. Shape: **monotonic, power-law, no hump.**

### Crosstalk that IS published — but the wrong kind
Choi et al., *"Spectator-transition crosstalk in a spin-3/2 silicon vacancy qudit in silicon carbide revealed by broadband Ramsey interferometry,"* arXiv:2601.15559 (submitted Jan 2026, revised June 2026), explicitly reports and quantifies crosstalk in VSi centers. Confirmed by direct check of the abstract: this crosstalk is **strictly intramolecular** — short, detuned control pulses coherently drive "non-addressed level pairs" within the multilevel spin-3/2 structure of a *single* defect (mapped to pairwise energy differences between qudit levels), not crosstalk between two spatially separated, individually-addressed defects. This mirrors exactly the distinction already flagged in the diamond scoping note between "many spatially separated NV centers addressed in parallel" vs. "multiplexing within a single NV center via hyperfine-coupled nuclear spins" — a recurring pattern worth remembering: most "crosstalk" language in this literature describes intra-defect spectral crosstalk, not inter-defect spatial crosstalk. **No spacing/density dependence of this crosstalk mode is reported or implied in the abstract.**

Separately, about a third of c-axis-oriented divacancies have a ²⁹Si nuclear-spin register on nearest-neighbor lattice sites, usable as auxiliary qubits via hyperfine coupling to the electron spin — again a within-single-defect multiplexing axis, not a spacing-between-defects axis. ([search summary of SiC divacancy quantum memory literature](https://arxiv.org/pdf/2005.07602))

### Verdict for SiC
Real, quantitative, monotonic density-vs-decoherence curve (T₁⁻¹∝C²) — same axis as diamond, not the wanted curve, but the cleanest fitted functional form found in this whole scoping pass. No true spacing-vs-inter-defect-crosstalk curve found.

---

## 2. Silicon color centers: T center and G center

### Why it's real and credible
T centers (a carbon-carbon-hydrogen complex, (C-C-H)Si) and G centers (two substitutional carbon atoms bonded to an interstitial silicon atom) are real, actively researched, telecom-O-band-emitting defects in silicon, notable for compatibility with existing silicon photonic integrated circuit (PIC) fabrication. T centers carry a spin-photon interface plus up to three nuclear spin qubits in a local register; single T centers have been integrated with silicon nanophotonics and Purcell-enhanced in nanocavities. G centers are described as the brightest of the known silicon telecom emitters and can be isolated at the single-defect level in unstructured SOI wafers. ([PRX Quantum review](https://link.aps.org/doi/10.1103/PRXQuantum.5.010102), [photonic.com T-center overview](https://photonic.com/blog/what-is-a-t-centre/), [arXiv:2405.07144](https://arxiv.org/pdf/2405.07144))

### No defect-defect spacing/crosstalk curve found
Despite a specific search for T/G-center array density, spacing, and crosstalk, no published spacing-vs-crosstalk or spacing-vs-reliability curve for T- or G-center *qubits themselves* was found. This is a real and honest gap, not a search-coverage failure to gloss over: the field is at an earlier stage than diamond NV or SiC divacancy — current work centers on single-defect isolation, brightness, spectral diffusion, and electrical/optical manipulation of individual centers, not yet ensemble/array-density characterization where a spacing-crosstalk sweep would even be measurable. ([arXiv:2311.08276](https://arxiv.org/pdf/2311.08276), [arXiv:2504.09908](https://arxiv.org/pdf/2504.09908) on T-centre spectral diffusion)

### A real but *adjacent* curve, flagged clearly as NOT the same thing
Silicon photonic waveguide crosstalk vs. pitch is a mature, well-quantified engineering literature: crosstalk rises exponentially as waveguide spacing shrinks below the wavelength scale, with reported figures such as <-20 dB crosstalk at 840 nm center-to-center spacing for coupled strip waveguides, and engineered sub-wavelength strip arrays pushing usable spacing down to 300–450 nm. This is a real, monotonic (exponential), well-characterized spacing-vs-crosstalk relationship — **but it describes on-chip optical *routing* crosstalk between waveguides carrying photons to/from color centers, not quantum crosstalk between the color-center defects themselves.** Including it without this caveat would misrepresent the finding; it is cited here only as a real, adjacent, enabling-technology data point that a future PIC-integrated T/G-center array would have to engineer around, not as defect-defect physics. ([ResearchGate summary of waveguide-array crosstalk papers](https://www.researchgate.net/publication/333982813_Design_of_a_low-crosstalk_half-wavelength_pitch_nano-structured_silicon_waveguide_array))

### Verdict for T/G centers
Real, credible, telecom-relevant platform; no defect-defect spacing/crosstalk curve exists yet in the literature searched — an honest gap tied to the field's early single-defect-characterization stage.

---

## 3. Hexagonal boron nitride (hBN) spin defects

Not on the original candidate list but genuinely real, credible, and directly relevant — included because it produced the two most useful data points of this whole pass.

### Density vs. coherence: same monotonic axis, with an actual fitted exponent
Gong et al., *"Coherent dynamics of strongly interacting electronic spin defects in hexagonal boron nitride,"* Nature Communications 14, 3299 (2023), measured negatively-charged boron-vacancy (V_B⁻) defect ensembles at three densities (dosages 0.30, 1.1, 10 nm⁻²; corresponding V_B⁻ densities 123, 149, 236 ppm) and found:

- T₂^XY8 decreasing monotonically with density: 250±35 ns → ~200 ns → 167±10 ns
- Fitted scaling **T₂ ∝ ρ⁻ᵅ, α ≈ 0.8 ± 0.1** for the XY-8 dynamical-decoupling sequence — a **power-law decay**, driven by V_B⁻–V_B⁻ dipolar interactions (confirmed via ~2x improvement from DROID decoupling, which specifically suppresses that dipolar term)
- No addressing-error or inter-defect crosstalk metric reported directly

Shape: **monotonic power-law, no hump** — the same family as the SiC and diamond density-decoherence curves. ([Nature Communications](https://www.nature.com/articles/s41467-023-39030-x) — accessed via PMC10244381)

### The closest real analog to a genuine spacing-vs-crosstalk curve found in this entire pass
Li, Pershin & Gali, *"Quantum Emission from Coupled Spin Pairs in Hexagonal Boron Nitride,"* arXiv:2408.13515 (Sept 2024; published Nature Communications 2025), studies donor-acceptor defect **pairs** (e.g., carbon-related CB donor coupled to an oxygen-substituted nitrogen-vacancy, ONVB, acceptor) as an explicit function of their separation distance. This is a genuinely distance-resolved study of two individually-identifiable, coupled defects — structurally the closest thing found to "spacing between adjacent addressable channels vs. reliability" for any alternative host. Key reported relationships:

- **Zero-phonon-line energy vs. distance: non-monotonic-flavored.** At short separations (closest sites, CB1/CB2) the ZPL is far into the UV (3.7–3.9 eV); at intermediate-to-large separations (CB3–CB5) it converges back down toward the isolated-defect value (~1.97 eV). This is a convergence-from-an-extreme shape, not a simple monotonic rise or fall from zero.
- **Metastable (dim) state energy vs. distance — explicit closed form, Coulombic**: E(Rᵢ) = E_gap − (E_D + E_A) + e²/(εRᵢ) — an inverse-distance (1/R) term causing rapid convergence to the charge-transfer-level difference (1.27 eV) at large R.
- **Spin-exchange (J-coupling) vs. distance**: reported scaling as **R⁻⁶** — steep, short-range-dominated.
- **Internal-conversion (non-radiative decay) rate vs. distance**: falls off approximately exponentially with orbital overlap, from ~10¹⁰ MHz at sub-1 nm separation down to 6–8 MHz at ~1.8 nm (18 Å).
- **Stated critical design window**: the authors report that CB–ONVB pairs need **roughly ≥2 nm separation** to show observable ODMR (optically detected magnetic resonance) signal while retaining a competitive radiative-to-non-radiative branching ratio — i.e., there is a real **threshold distance below which the pair is not usable as two separately addressable qubits at all** (non-radiative/exchange pathways dominate), with properties then converging smoothly toward isolated single-defect behavior as separation increases further.

**Honest characterization of the shape:** this is neither the photonic curve's shape (smooth monotonic/saturating error-rate-vs-spacing from a continuous sweep) nor the phononic curve's shape (non-monotonic hump peaking at an interior dimerization value). It is closer to a **threshold/critical-window curve**: unusable below ~2 nm, then asymptotically converging (via 1/R Coulomb and e⁻ᴿ tunneling terms) toward isolated-defect values above that threshold. This is flagged as a real, distinct third shape category worth carrying into the cross-substrate framework, though with the caveat that it describes an engineered *donor-acceptor pair* (two chemically distinct, coupled defect species), not an ensemble of identical, individually-addressed channels the way the photonic and phononic curves do — the comparison is suggestive, not a clean apples-to-apples match. ([arXiv:2408.13515v2](https://arxiv.org/html/2408.13515v2))

---

## The topological/phase-transition question: a real, clean negative result

A specific, repeated search for any theoretical connection between point-defect spin qubits (diamond, SiC, hBN, or silicon T/G centers) and topological protection or topological phase transitions found **nothing**. Every "topological" hit returned across multiple search queries was about unrelated photonic-crystal metamaterial band topology (e.g., pseudospin-locked edge states in rotated-rod photonic crystals) — a completely different physical system (engineered periodic dielectric structures), not point defects in a crystal lattice. No paper was found proposing that NV-like defect qubits inherit any topological/symmetry-protected structure analogous to the phononic SSH system's chiral-symmetry-protected edge modes.

This is reported as a genuine, confirmed absence rather than a search-coverage gap to hedge on, because it is consistent with basic physical reasoning that a future write-up can state with confidence: NV-like point defects are simple two-level (or few-level, e.g. spin-3/2 qudit) optically-addressable spin systems with no band structure and no topological invariant to protect. Their crosstalk/reliability mechanisms — dipolar bath coupling, spectral-transition mixing, Coulomb/exchange/tunneling overlap between pairs — are all "ordinary" short-range physical couplings that fall off smoothly with distance (power-law, exponential, or 1/R), which is exactly why every density/spacing curve found across diamond, SiC, and hBN in this pass (and the prior one) is monotonic. The one candidate for a non-monotonic shape (the hBN donor-acceptor threshold window) arises from ordinary competition between radiative and non-radiative decay channels as a function of wavefunction overlap, not from any topological mechanism — its threshold shape is real but mechanistically unrelated to the phononic hump, which is specifically a chiral-symmetry/dimerization effect. **If the theoretical framework being built in parallel wants a topologically-protected point-defect-qubit substrate, none currently exists in the literature searched here; it would be a novel theoretical proposal, not a literature-grounded claim.**

---

## Summary table

| Host | Real density/spacing curve found? | Shape | Same axis as wanted (inter-channel crosstalk)? | Topological connection? |
|---|---|---|---|---|
| SiC divacancy/VSi | Yes — T₁⁻¹ = βC² (quadratic) | Monotonic power-law | No — bath decoherence, not inter-defect crosstalk | None found |
| Silicon T/G centers | No defect-defect curve found | N/A (field too early-stage) | N/A | None found |
| hBN V_B⁻ ensembles | Yes — T₂ ∝ ρ⁻⁰·⁸ | Monotonic power-law | No — same bath-decoherence axis | None found |
| hBN donor-acceptor pairs | Yes — ZPL/energy/rate vs. distance, multiple functional forms | Threshold/critical-window, then asymptotic convergence | Closest analog found, but pair-specific, not ensemble/array crosstalk | None found |

**Recommendation for the parallel synthesis effort:** none of these three alternative hosts supplies a clean, ready-to-use "inter-channel crosstalk vs. spacing" curve of the photonic or phononic type. The hBN donor-acceptor-pair result (Li, Pershin & Gali 2024) is the best available real candidate if a third data point is needed, but it should be clearly labeled as a *pair-coupling* curve (two coupled, chemically-distinct defects) rather than an *array* curve (many identical, individually-addressed channels), to avoid the same unmatched-resolution/confound problem already flagged for the ferroelectric domain-size comparison in the prior scoping note. The clean, confirmed negative result — no topological connection exists for any point-defect qubit host in the current literature — is itself a useful, honest boundary condition for the theoretical framework: topological protection, if it belongs anywhere in this cross-substrate picture, belongs to the phononic/photonic-crystal side, not to point-defect spin qubits.

---

## Sources

**SiC divacancy / VSi:**
- [Room-temperature coherent manipulation of single-spin qubits in silicon carbide with a high readout contrast, PMC9160373](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9160373/)
- [Control of spin defects in wide band-gap semiconductors, OSTI](https://www.osti.gov/pages/servlets/purl/1339658)
- [Dipolar spin relaxation of divacancy qubits in silicon carbide, npj Computational Materials / arXiv:2102.01782](https://www.nature.com/articles/s41524-021-00673-8)
- [Spectator-transition crosstalk in a spin-3/2 silicon vacancy qudit in silicon carbide revealed by broadband Ramsey interferometry, arXiv:2601.15559](https://arxiv.org/abs/2601.15559)
- [Entanglement and control of single quantum memories in isotopically engineered silicon carbide, arXiv:2005.07602](https://arxiv.org/pdf/2005.07602)

**Silicon T/G centers:**
- [Scalable Fault-Tolerant Quantum Technologies with Silicon Color Centers, PRX Quantum 5, 010102](https://link.aps.org/doi/10.1103/PRXQuantum.5.010102)
- [What Is a T Centre? Unique Silicon Spin-Photon Qubits](https://photonic.com/blog/what-is-a-t-centre/)
- [Optical transition parameters of the silicon T centre, arXiv:2405.07144](https://arxiv.org/pdf/2405.07144)
- [Electrical manipulation of telecom color centers in silicon, arXiv:2311.08276 / Nature Communications](https://www.nature.com/articles/s41467-024-48968-w)
- [Laser-induced spectral diffusion and excited-state mixing of silicon T centres, arXiv:2504.09908](https://arxiv.org/pdf/2504.09908)
- [Design of a low-crosstalk half-wavelength pitch nano-structured silicon waveguide array](https://www.researchgate.net/publication/333982813_Design_of_a_low-crosstalk_half-wavelength_pitch_nano-structured_silicon_waveguide_array)

**hBN spin defects:**
- [Coherent dynamics of strongly interacting electronic spin defects in hexagonal boron nitride, Nature Communications 14, 3299 (2023)](https://pmc.ncbi.nlm.nih.gov/articles/PMC10244381/)
- [Quantum Emission from Coupled Spin Pairs in Hexagonal Boron Nitride, arXiv:2408.13515](https://arxiv.org/html/2408.13515v2)
- [Narrowband quantum emitters in hexagonal boron nitride with optically addressable spins, Nature Materials](https://www.nature.com/articles/s41563-025-02458-6)

**Topological search (negative result):**
- Search queries covering "topological point defect qubit," "topological protection color center," and "symmetry-protected spin defect diamond/SiC/hBN" returned only unrelated photonic-crystal-metamaterial topology results (e.g., pseudospin-locked photonic crystal edge states) — no point-defect-qubit topological connection found in any source surfaced.
