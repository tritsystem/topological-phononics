# Scoping two candidate crystal memory substrates: NV centers in diamond and ferroelectric/piezoelectric crystal memory

**tritsystem** (independent researcher), 2026-08-21
Companion scoping note to `META_LEDGER.md`'s crystal-substrate candidate survey (that entry triaged these two as "tied — real, well-established, zero existing account data" and flagged this as the needed from-scratch follow-up). **This is not a synthesis attempt and contains no simulation or new measurement.** It is a literature-grounded scoping pass for two candidates, done the same way the photonic spectral-hole-burning work and the acoustic/phononic work were grounded before any comparison was attempted: real citable sources, explicit flags on what's confirmed vs. general domain knowledge vs. genuinely uncertain, and an honest answer to the one question that actually matters for a future synthesis — does a real, published "density/spacing vs. reliability" curve already exist for either substrate, comparable in shape to the photonic BER-vs-channel-spacing curve (50% error at 0.05x linewidth spacing down to 0.09% at 1x spacing, from the spectral-hole-burning work)?

**Bottom line up front: no. Neither substrate has a published curve of that structural type readily available in the literature searched here.** Both fields have real, quantitative density/reliability data, but it is not shaped as a continuous "spacing parameter vs. error-rate" sweep the way the photonic result is. Details and the closest real approximations each field offers are below.

---

## 1. NV centers in diamond

### Physical mechanism (confirmed via sources)

The negatively charged nitrogen-vacancy (NV⁻) center is a point defect (a substitutional nitrogen atom adjacent to a lattice vacancy) with a spin-triplet ground state. Information is stored in the electron spin state, which is optically initialized (spin-polarized) and read out via spin-dependent fluorescence intensity — this is confirmed across all sources reviewed and matches domain knowledge; nothing here contradicts the standard picture. Beyond the electron spin, nearby nuclear spins (host ¹⁴N/¹⁵N, and ¹³C in the surrounding lattice) can be individually addressed and used as auxiliary qubits/memory via the electron spin as an intermediary — this is the basis of the multi-qubit "register" results below.

### State of the art: coherence times

- Room/near-room-temperature ensemble T2\* is short and set by the nitrogen (P1) electron-spin bath: reported values range from ~118 ns in high-NV-density diamond (NV⁻ ≈ 16 ppm, N_s⁰ ≈ 49 ppm) up to ~600 µs in low-nitrogen-density (~10¹⁵ cm⁻³) isotopically-controlled samples. ([Decoherence of NV spin ensembles, npj Quantum Information](https://www.nature.com/articles/s41534-022-00605-4); [arXiv:2503.05404](https://arxiv.org/pdf/2503.05404))
- Single-NV T2\* of 1.5 µs extended to ~200 µs via dynamical decoupling has been reported; a related technique (microwave-dressed states) reported T2 ~1.5 ms, over two orders of magnitude longer than the undressed state. ([Scientific Reports](https://www.nature.com/articles/s41598-019-49683-z))
- Individual nuclear-spin qubits with coherence "exceeding seconds" were reported in a 2025 Nature Physics paper — this is a strong, recent claim worth flagging as important but I have not independently verified the operating conditions (temperature, isolation) beyond the search snippet; treat as **reported, not independently cross-checked here**. ([Nature Physics](https://www.nature.com/articles/s41567-025-03049-7))
- A related defect, the germanium-vacancy (GeV) center, was reported reaching 20 ms coherence, a ~45x extension over comparable NV baselines — cited here as a real adjacent-platform data point, not as an NV-center number itself. ([phys.org / GeV coherence report](https://phys.org/news/2024-02-diamond-quantum-memory-germanium-vacancy.html))

**Honest read:** there is a genuine, well-documented density-vs-coherence tradeoff (more nitrogen → easier NV formation and stronger signal, but faster decoherence from the P1 spin bath), quantified in dipolar interaction strength terms: mean P1-bath interaction strength ranges from ~1.46 kHz at 1 ppm nitrogen to ~437 kHz at 300 ppm. ([arXiv:2503.05404](https://arxiv.org/pdf/2503.05404)) This is the closest thing in this field to the photonic "spacing vs. error" curve, but it relates *dopant concentration* to *coherence time*, not *inter-channel spacing* to *readout/crosstalk error rate* — a related but structurally different axis (see "comparable curve" verdict below).

### State of the art: multiplexing / channel capacity

- A 2024 paper demonstrated parallel manipulation and measurement of **over 100 NV centers simultaneously** (108 in the reported dataset, yielding 5,778 simultaneous pairwise correlation measurements), with the authors stating the platform "can be scaled to parallel experiments with thousands of individually resolved NV centers," with the ultimate limit set by optical crosstalk and the microscope's field of view. ([arXiv:2408.11715](https://arxiv.org/abs/2408.11715), published version [PRX](https://journals.aps.org/prx/pdf/10.1103/jdzq-jbfz))
- A separate, well-known multi-qubit result: a single NV electron spin used as a hub to control and entangle **up to 10 qubits** (the electron spin plus 9 nuclear spins), with genuine multipartite entanglement demonstrated up to 7 qubits, and control extended to **up to 27 nuclear spins** around a single NV center in follow-on work. ([arXiv:1905.02094](https://arxiv.org/pdf/1905.02094), [PRX](https://link.aps.org/doi/10.1103/PhysRevX.9.031045), companion imaging paper [arXiv:1905.02095](https://arxiv.org/pdf/1905.02095)) **Important distinction, confirmed from the abstracts:** this is multiplexing *within a single optically-addressed NV center* via hyperfine coupling to surrounding nuclear spins — a different multiplexing axis from the "many spatially-separated NV centers addressed in parallel" result above. A future study comparing this to spectral-hole channel-packing should be careful not to conflate the two.

### Is there a real, published "spacing vs. crosstalk/error" curve?

**Not found in a form structurally comparable to the photonic result.** The parallel-measurement paper explicitly discusses crosstalk mechanisms — optical pulses aimed at one NV can perturb neighboring NVs' spin and (to a lesser extent) charge states, and spin-correlation-spectroscopy pulses were observed to re-polarize nearby NV spins, reducing signal-to-noise for close-together centers — but reports this qualitatively and via a scalability ceiling (~9,000 achievable before crosstalk/field-of-view becomes limiting), **not** as a continuous swept curve of "spacing distance vs. quantified error rate." ([arXiv:2408.11715](https://arxiv.org/html/2408.11715)) A separate optical demultiplexer result for NV-based signal routing reports ~96% channel-spacing figure and 17 ns switching speed, but this describes a specific device's isolation performance at one operating point, not a swept curve either. ([PMC8623633](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8623633/)) This gap should be stated plainly: **the literature searched here does not contain a directly comparable multi-point spacing-vs-error sweep for NV centers.** It may well exist in papers not surfaced by this search (e.g., dedicated NV-array crosstalk characterization papers), and a deeper literature dive focused specifically on that question would be the right next step before assuming the gap is real rather than a search-coverage artifact.

### Real current limitations

- **Temperature:** high-fidelity single-shot readout currently requires cryogenic operation (commonly ~8 K in the cited work) using spin-to-charge conversion or resonant excitation; simple room-temperature optical readout exists but is comparatively inefficient — contrast between spin states is short-lived (~250 ns) and low (~30%). Room-temperature *sensing* applications of NV centers are mature; room-temperature *high-fidelity single-shot readout for information storage* is the harder, less-solved regime. ([PMC7822820](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7822820/), [Nature Communications](https://www.nature.com/articles/s41467-021-21781-5))
- **Readout fidelity:** single-shot electron-spin readout fidelity >95% has been reported under favorable conditions (spin-to-charge conversion); single- and two-qubit gate fidelities of 99.99%/99.2% have also been reported — these are strong numbers but are best-case, specific-apparatus results, not yet a general fabrication-line baseline.
- **Fabrication yield:** a "high creation yield of NV centers of 75%" was reported via charge-assisted defect engineering, described as a tenfold enhancement over prior methods — implying baseline yields have historically been low (roughly single-digit percent), which is a real, current fabrication bottleneck.
- **The core physical tension:** the same nitrogen doping needed to create NV centers also creates the P1 spin bath that limits coherence — this tradeoff is fundamental to the material system, not an engineering detail expected to disappear with better fabrication alone.

---

## 2. Ferroelectric / piezoelectric crystal memory

### Physical mechanism (confirmed via sources)

Ferroelectric materials have two (or more) stable, remanent spontaneous polarization states, switchable by an applied electric field exceeding a coercive threshold; the bistable polarization state (not a charge or current) is the stored bit, read either via a destructive polarization-reversal current pulse (classic FeRAM) or non-destructively via a ferroelectric field-effect transistor (FeFET) channel-conductance readout. This matches the standard picture and is confirmed as accurate across the sources reviewed.

### State of the art: is this mature deployed tech or active research, or both?

**Both, cleanly separable:**

- **Mature/deployed:** Classic perovskite (PZT, SBT) FeRAM is a real, shipping technology (embedded and standalone), with Fujitsu named as actively shipping FeRAM chips for automotive applications in 2024. Current commercial densities are modest — reported in the 4–8 Mb range, well below multi-gigabit NAND flash densities — which is *the* reason FeRAM has stayed a niche (low-power, high-endurance, non-volatile) rather than a bulk-storage technology. ([market/industry summary sources, see Sources list])
- **Active research frontier:** HfO₂-based (and HfZrO₂, "HZO") ferroelectrics are the real current research push, because they are CMOS-compatible (unlike PZT) and enable aggressive scaling. Concrete, recent, quantitative results:
  - CEA-Leti demonstrated a scalable HZO-based embedded FeRAM platform at the **22 nm FD-SOI node** (Dec 2024).
  - BEOL-integrated 16 kb HfO₂:Si FeRAM arrays reported **4 ns programming speed, 10⁷-cycle endurance, 125°C retention**.
  - More advanced HZO devices reported endurance **exceeding 10¹²cycles** with improved breakdown tolerance.
  - Stable ferroelectric switching has been reported in films **below 3 nm thick**, and reliable fast switching in **5 nm-thick HZO**, supporting continued scaling.
  - Sub-5 V write voltage and <10 ns switching reported for HfO₂-based FeFETs.
  - A distinct, mechanistically different 2024 Science paper reported **ultrafast, high-endurance memory based on "sliding ferroelectrics"** (interlayer-sliding polarization switching in van der Waals materials) — flagged here as a genuinely different mechanism from bulk-perovskite or HfO₂ ionic-displacement ferroelectricity, and a real, separate research thread worth distinguishing in any future write-up. I was not able to fetch the full text directly (403 on the publisher page) so the specific numbers are not independently re-verified here beyond the search-summary level — **treat the existence and general claim as confirmed, the exact quoted figures as unverified pending a direct read.**
  - Multiferroic/magnetoelectric memory (electric-field control of magnetism via a coupled ferroelectric-ferromagnetic heterostructure) is a real, separate, less mature research area — electric write + magnetic read (or vice versa) is the appealing property, and room-temperature robust magnetoelectric coupling is described as still an open target ("hope that robust electric control of magnetism at room temperature will be achieved soon" — i.e., not yet routinely achieved as of the sources reviewed).

### Is there a real, published domain/bit-spacing vs. reliability curve?

**Partially — closer to comparable than the NV case, but still not the same curve shape.** Two real, quantitative, but distinct data points were found:

1. A direct **domain-size vs. reliability** comparison: Y-doped HfO₂ devices with a measured domain size of **5.64 nm** were compared against Si-doped devices with domain size **12.47 nm**, with the larger-domain devices showing better constant-voltage-stress time-to-breakdown and cycle-to-breakdown stability — i.e., a real, quantified, two-point relationship between physical domain size and reliability. ([PMC10386612](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10386612/)) This is a genuine density-vs-reliability data point, but it is two discrete material variants, not a continuous sweep, and it conflates domain size with dopant species (a confound a future comparison would need to be aware of — this is exactly the kind of unmatched-resolution problem that sank the acoustic/photonic comparison in `META_LEDGER.md` row #22).
2. A **crosstalk mechanism paper** on arrays of ferroelectric nanocapacitors reports that under typical switching pulses the switched domain stays confined within its own capacitor, but under longer or higher-bias pulses, domain walls propagate into neighboring capacitors, and this propagation is described as reproducible (same paths/area on repeated runs) and material-defect-dependent — but **no quantitative pitch/spacing-vs-crosstalk-magnitude curve is given**, only the qualitative mechanism. ([arXiv:1110.5614](https://arxiv.org/abs/1110.5614))
3. A ferroelectric domain-wall-memory roadmap review states domain wall thickness can approach ~1 nm (near the unit-cell level) and cites sub-20 nm memory cells demonstrated in lithium niobate, with a projected 4F² cell footprint — real density-relevant numbers — but again **no explicit spacing-vs-error-rate functional curve** is reported in the review; crosstalk mitigation is discussed only architecturally (selector devices, diode-like rectification giving on/off ratios around 100 at 3V), not as a swept reliability curve. ([oaepublish.com roadmap review](https://www.oaepublish.com/articles/microstructures.2023.52))

**Honest verdict: no continuous, multi-point "spacing vs. error-rate" sweep of the photonic type was found for ferroelectric memory either**, but the field is closer than NV centers in one respect — the domain-size-vs.-reliability two-point comparison (#1 above) is at least the same *kind* of relationship (physical feature size vs. failure probability), just not resolved at more than two points and confounded with dopant chemistry.

### Real current limitations

- **Endurance/retention tradeoff:** high endurance (>10¹² cycles in the best HZO reports) has historically required over a decade of interfacial-layer optimization; FeFET retention is challenged by a depolarization field that can be large relative to the coercive field, plus charge trapping at imperfect interfaces — these are described as still-active engineering problems, not fully solved.
- **Density ceiling (classic FeRAM):** commercial PZT/SBT FeRAM density is genuinely capped well below flash-competitive levels (Mb-scale vs Gb-scale), which is why it has stayed a niche low-power/high-endurance product rather than displacing flash.
- **Scaling vs. CMOS compatibility:** classic perovskite ferroelectrics need high-temperature deposition incompatible with modern CMOS back-end processing — this is the specific reason HfO₂/HZO (which is CMOS-compatible and scales to sub-5 nm films) is the active research direction rather than further scaling of PZT.
- **Multiferroics specifically:** robust room-temperature magnetoelectric coupling is described in the literature as still not routinely achieved — this is the field's central open problem, not a solved capability being merely optimized.

---

## Direct answer to the key question (both substrates)

Neither NV centers in diamond nor ferroelectric/piezoelectric crystal memory has a readily available, published, continuous "density/spacing vs. reliability-or-crosstalk" curve that is structurally comparable to the photonic spectral-hole-burning bit-error-rate-vs-channel-spacing curve (the 8-point sweep from 0.05x to 10x linewidth, 50%→0.09% error). This is stated honestly rather than force-fit:

- **NV centers:** real crosstalk mechanisms are documented and a scalability ceiling (~9,000 parallel centers) is reported, but as qualitative descriptions and a single scaling estimate, not a swept curve. The closest quantitative analog found is dopant-concentration-vs-coherence-time (a real, multi-point relationship, e.g., 1 ppm→1.46 kHz interaction strength up to 300 ppm→437 kHz), which is a genuine density/reliability tradeoff but answers a different physical question (bath-induced decoherence, not inter-channel readout crosstalk).
- **Ferroelectric memory:** a real two-point domain-size-vs.-reliability comparison exists (5.64 nm vs 12.47 nm domain size, larger domains more stable), which is closer in *kind* to what's wanted, but it is two data points confounded with dopant species, not a resolved continuous sweep, and no explicit bit-pitch-vs-crosstalk curve was found despite the mechanism (domain-wall propagation into neighboring cells) being well documented qualitatively.

**Recommendation for a future synthesis attempt:** treat both as needing new work before a row like `META_LEDGER.md` #22/#23 could be attempted honestly. Two honest paths forward, in order of effort: (a) a deeper, more targeted literature search specifically for NV-array crosstalk characterization papers and ferroelectric bit-pitch reliability studies (this pass was broad-scope triage, not exhaustive — a dedicated search might still surface a real curve that wasn't found here), or (b) if no such curve exists anywhere in the literature, that is itself the honest finding — these substrates would need a real (simulated or literature-meta-analysis-derived) density-vs-error dataset built from scratch before any comparison to the photonic result would be measurable rather than force-fit, exactly the failure mode row #22 already documented once.

---

## Sources

**NV centers — coherence, mechanism, multiplexing:**
- [Decoherence of nitrogen-vacancy spin ensembles in a nitrogen electron-nuclear spin bath in diamond, npj Quantum Information](https://www.nature.com/articles/s41534-022-00605-4)
- [Quantum decoherence of NV spin ensembles in a nitrogen spin bath, arXiv:2503.05404](https://arxiv.org/pdf/2503.05404)
- [Extension of the Coherence Time by Generating MW Dressed States in a Single NV Centre in Diamond, Scientific Reports](https://www.nature.com/articles/s41598-019-49683-z)
- [Individual solid-state nuclear spin qubits with coherence exceeding seconds, Nature Physics (2025)](https://www.nature.com/articles/s41567-025-03049-7)
- [Diamond quantum memory with Germanium vacancy exceeds coherence time of 20 ms, phys.org](https://phys.org/news/2024-02-diamond-quantum-memory-germanium-vacancy.html)
- [Scalable parallel measurement of individual nitrogen-vacancy centers, arXiv:2408.11715](https://arxiv.org/abs/2408.11715) / [PRX version](https://journals.aps.org/prx/pdf/10.1103/jdzq-jbfz)
- [Demultiplexer of Multi-Order Correlation Interference in Nitrogen Vacancy Center Diamond, PMC8623633](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8623633/)
- [A 10-qubit solid-state spin register with quantum memory up to one minute, arXiv:1905.02094](https://arxiv.org/pdf/1905.02094) / [PRX 9, 031045 (2019)](https://link.aps.org/doi/10.1103/PhysRevX.9.031045)
- [Atomic-scale imaging of a 27-nuclear-spin cluster using a single-spin quantum sensor, arXiv:1905.02095](https://arxiv.org/pdf/1905.02095)
- [Robust all-optical single-shot readout of nitrogen-vacancy centers in diamond, PMC7822820](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7822820/)
- [High-fidelity single-shot readout of single electron spin in diamond with spin-to-charge conversion, Nature Communications](https://www.nature.com/articles/s41467-021-21781-5)
- [A review of the study of diamond NV color centers: fabrication, application and challenge (2025)](https://www.tandfonline.com/doi/full/10.1080/26941112.2025.2567286) — cited from search-result summary only; full text returned HTTP 403 on direct fetch and was not independently re-verified beyond the search snippet.

**Ferroelectric / piezoelectric memory:**
- [Comprehensive Investigation of Constant Voltage Stress Time-Dependent Breakdown and Cycle-to-Breakdown Reliability in Y-Doped and Si-Doped HfO2 Metal-Ferroelectric-Metal Memory, PMC10386612](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10386612/)
- [Cross talk by extensive domain wall motion in arrays of ferroelectric nanocapacitors, arXiv:1110.5614](https://arxiv.org/abs/1110.5614)
- [Roadmap for ferroelectric domain wall memory, Microstructures (2023)](https://www.oaepublish.com/articles/microstructures.2023.52)
- [Advancing the Frontiers of HfO2-Based Ferroelectric Memories: Innovative Concepts from Materials to Applications, Advanced Materials (2025)](https://advanced.onlinelibrary.wiley.com/doi/10.1002/adma.202509525) — cited from search-result summary only; full text returned HTTP 403 on direct fetch.
- [Ultrafast high-endurance memory based on sliding ferroelectrics, Science (2024)](https://www.science.org/doi/10.1126/science.adp3575) — cited from search-result summary only; full text returned HTTP 403 on direct fetch, specific numbers not independently re-verified.
- [Hafnium oxide-based ferroelectric field effect transistors: From materials and reliability to applications in storage-class memory and in-memory computing, Journal of Applied Physics](https://pubs.aip.org/aip/jap/article/138/1/010701/3351745/Hafnium-oxide-based-ferroelectric-field-effect)
- [HfO2-based ferroelectric thin film and memory device applications in the post-Moore era: A review, PMC11197553](https://pmc.ncbi.nlm.nih.gov/articles/PMC11197553/)
- [Multiferroics: different routes to magnetoelectric coupling, npj Spintronics (2024)](https://www.nature.com/articles/s44306-024-00021-8)
- [Magnetoelectric Memory Based on Ferromagnetic/Ferroelectric Multiferroic Heterostructure, PMC8401036](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8401036/)
- [Reviewing multiferroics for future, low-energy data storage, ScienceDaily (2020)](https://www.sciencedaily.com/releases/2020/10/201022112622.htm)
- FeRAM commercial density/market context (4-8 Mb typical commercial density, Fujitsu 2024 automotive FeRAM, CEA-Leti 22nm FD-SOI HZO FeRAM Dec 2024): drawn from industry/market-report search summaries (patsnap, market-research aggregators) rather than a single primary source — **flagged as lower-confidence than the peer-reviewed citations above; worth independently confirming the CEA-Leti and Fujitsu claims directly from CEA-Leti/Fujitsu press material before relying on them for a quantitative future study.**

## What's confirmed vs. uncertain — explicit summary

- **Confirmed (peer-reviewed primary or near-primary source, cross-checked description):** NV spin-state storage/readout mechanism; ferroelectric bistable-polarization mechanism; the ppm-vs-coherence-time NV tradeoff numbers; the >100-NV parallel measurement result and its stated ~9,000-center scaling ceiling; the 10-qubit/27-nuclear-spin NV register results; the HfO₂/HZO endurance, retention, and film-thickness scaling numbers; the 5.64 nm vs 12.47 nm domain-size reliability comparison; the qualitative domain-wall-propagation crosstalk mechanism.
- **Reported but not independently re-verified here (search-snippet level only, direct fetch blocked):** the NV color-center review (tandfonline), the Advanced Materials HfO₂ review, and the sliding-ferroelectrics Science paper's exact quoted numbers. These are flagged, not silently treated as confirmed.
- **Genuinely uncertain / actively contested or unsettled in the field itself (not just uncertain to this search):** room-temperature high-fidelity single-shot NV readout for storage (vs. sensing) remains harder than cryogenic readout; robust room-temperature magnetoelectric coupling in multiferroics is explicitly described in the literature as not yet routinely achieved; NV fabrication yield, even after a reported "tenfold enhancement," implies historically low baseline yields that are not fully resolved.
- **The central honest negative finding of this whole scoping pass:** no directly comparable continuous "spacing/density vs. reliability" curve was found for either substrate. This may reflect a real gap in the public literature, or may reflect the limits of this particular (broad, not exhaustive) search pass — the two possibilities were not distinguished here and should not be conflated in any future write-up that cites this document.
