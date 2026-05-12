# Causal Perturbation Genomics of Exercise and Biological Ageing

**Ciara G. Juan — PhD Thesis, Ulster University, 2026**  
*Faculty of Life and Health Sciences · Supervisors: Professor Gareth Davison · Dr Kyle Matchett*

---

## What this thesis does

Most exercise genomics studies produce gene lists. This thesis builds a **causal perturbation framework** — integrating genetic causal inference, supervised graph learning, network-based in silico perturbation, and controlled human experimentation — to resolve *how* habitual vigorous physical activity reorganises molecular systems to shape long-term biological ageing in humans.

The central question is not which genes are associated with exercise. It is **which molecular pathways, when perturbed, propagate influence toward stable ageing-related molecular architecture** — and which merely buffer acute physiological stress without encoding ageing state.

---

## Framework overview

```
GWAS (n ≈ 75,000)
        ↓
LD-aware Mendelian Randomisation
[proteomics · epigenomics · glycomics · single-cell transcriptomics]
        ↓
Supervised Graph Attention Network (MR-GAT)
[causal inference × protein structure × functional topology]
        ↓
Self-supervised contrastive graph representation learning
+ MR-informed masked multi-task embedding refinement
        ↓
Acute in silico gene perturbation
+ PPR network diffusion
+ degree-matched null models
        ↓
Epigenetic and proteomic ageing clock evaluation
[Horvath · Hannum · PhenoAge · DunedinPACE · Proteomic Clock]
        ↓
Controlled human exercise intervention (RCT)
[DNA damage · repair gene expression · plasma glycomics · GlycanAge]
```

---

## Studies

### Study 1 — Meta-analysis of the SIRT1 response to exercise
*Published: Scientific Reports, 2023*

Systematic review and meta-analysis of 47 studies quantifying the SIRT1 response to exercise in humans. Establishes SIRT1 as an intensity- and energy-sensitive mediator linking physiological stress to DNA damage responses and genome maintenance. Provides the biological grounding for SIRT1 as a high-priority node in the downstream network framework.

---

### Study 2 — Supervised multi-omic graph neural network (MR-GAT)
*Preprint: medRxiv, https://doi.org/10.64898/2025.12.26.25343061*

The first deep learning, multi-omic framework for human exercise genomics. A supervised Graph Attention Network (GAT) integrates causal MR signals across four omic layers with AlphaFold v6 structural descriptors, UniProt/InterPro/PANTHER functional annotations, and kNN graph topology to prioritise exercise-responsive genes.

**Key design decisions:**
- Continuous multi-omic trait importance (MTI) score over binary p-value thresholds — preserves graded causal evidence and avoids saturation from high-powered proteomic layers
- Two-head architecture (MTI regression + multi-layer support classification) sharing gene embeddings — forces a unified latent representation
- MR ablation stress testing: full model vs no-MR vs MR-only (Spearman ρ = 0.875; 57–61% Jaccard overlap at top-K) — rules out the model simply recapitulating MR rankings
- Permutation-based ageing clock enrichment testing (empirical p > 0.1, FDR = 1.0) — confirms clock alignment is interpretative context, not supervised optimisation

**Findings:** Top 1,000 GNN-ranked genes organise into coherent genome maintenance modules spanning DNA repair, redox signalling, autophagy, proteostasis, immune regulation, circadian control, and glycosylation — substantially overlapping with biological ageing clock architecture.

---

### Study 3 — Acute in silico perturbation within a habitual exercise-adapted network
*Preprint: medRxiv, https://doi.org/10.64898/2026.02.01.26345311*

The first application of in silico network perturbation to human exercise biology. Single-event acute gene-level perturbations are simulated by modifying embedding vectors and propagated via Personalised PageRank diffusion within a network shaped by genetically proxied habitual vigorous physical activity. Perturbation effects are evaluated for alignment with epigenetic and proteomic ageing clocks using degree-matched null models — with no ageing supervision at any stage of training.

**Perturbation model:**
```
z_g' = (1 ± s) × z_g
Δ_g  = ||z_g' − z_g||₂
impact_i = p_i × Δ_g

PPR: p^(t+1) = (1 − α) e_g + α D⁻¹ A p^(t)
```

**Key finding:** A hierarchical network organisation distinguishes two classes of exercise-responsive genes:

| Gene class | Examples | Diffusion profile | Ageing clock alignment |
|---|---|---|---|
| Glycosylation enzymes | B4GALT1, ST6GAL1, ST3GAL1, ST3GAL4, MGAT3, MGAT5, MGAT5B | High Gini, low entropy (concentrated) | Enriched (p < 0.01) |
| DNA repair / stress response | PARP1, SIRT1, RAD51 | Low Gini, high entropy (diffuse) | Not enriched (p > 0.1) |

Glycosylation networks act as **proximal encoders of stable ageing-related molecular state**. DNA repair pathways act as **upstream buffers of acute physiological stress** — essential for genome integrity but not directly encoding ageing clock architecture. This resolves a long-standing ambiguity in damage-centric models of ageing.

---

### Study 4 — Randomised controlled crossover trial: exercise × quercetin
*Preprint: medRxiv, https://doi.org/10.1101/2025.10.31.25338366*

The first randomised, double-blind, placebo-controlled crossover trial combining high-intensity interval exercise (HIIE, ≈80% VO₂max) with three-week quercetin supplementation, quantifying DNA damage and repair alongside glycan-based biological ageing markers in healthy men.

**Key findings:**
- Acute HIIE increased DNA strand breaks, oxidised purine bases, and double-strand break signalling (γH2AX)
- SIRT1, PARP1, and RAD51 — independently prioritised by the MR-GAT — were significantly upregulated post-exercise, confirming a coordinated homologous recombination axis
- Quercetin preserved SIRT6 and OGG1 expression, reduced oxidative DNA damage, and promoted NRF2 nuclear translocation
- Acute exercise remodelled plasma galactosylation and sialylation (directionally consistent with younger glycan-based biological age); quercetin attenuated these acute plasma changes, consistent with redox buffering
- IgG GlycanAge (a temporally stable composite ageing biomarker) did not change acutely — confirming that stable biological ageing state is not directly encoded by acute stress responses

This experimental study provides biological grounding for the network hierarchy identified computationally in Study 3: DNA repair genes are acute responders; glycosylation networks encode integrative, stable ageing state.

---

## Unifying framework

The four studies converge on a single mechanistic model:

> Vigorous exercise generates short-lived ROS pulses that engage DNA repair and stress-response programmes (SIRT1, PARP1, RAD51, OGG1, SIRT6). These pathways act as adaptive buffers — high-centrality network nodes that resolve acute genomic volatility without themselves encoding long-term ageing state. Downstream, glycosylation networks integrate the cumulative immune-metabolic consequences of repeated exercise exposure, encoding stable molecular states captured by epigenetic and proteomic ageing clocks. Habitual exercise reinforces both layers — the acute repair buffer and the downstream ageing encoder — through repeated physiological stress and recovery.

This framework refines damage-centric models of ageing by distinguishing stress buffering from ageing state encoding at the network level, and establishes in silico perturbation as a principled approach to forecast how lifestyle exposures shape long-term biological ageing trajectories.

---

## Limitations and future directions

**Current limitations of the perturbation framework:**
- PPR diffusion is static and linear — does not capture non-linear regulation, feedback loops, or context-dependent effects
- Embedding perturbation z' = (1 ± s)z assumes proportional, direction-symmetric effects — not biologically realistic for all knockdowns
- Single-event acute perturbations only — combinatorial, dose-response, and temporal dynamics not modelled
- Graph topology is fixed and population-derived — does not adapt to cell-type context or disease state
- MLP encoder discards graph structure during contrastive pretraining — a scalable GNN encoder would capture neighbourhood information currently lost

**Natural extensions:**
- Repeated or temporally weighted perturbation schemes for cumulative exposure modelling
- Cell-type-resolved and tissue-specific interaction networks
- Integration of other genetically proxied exposures (diet, pharmacological interventions, disease liabilities)
- Extension to generative perturbation modelling over expression space
- Prospective validation in longitudinal exercise cohorts

---

## Code repositories

| Repository | Description |
|---|---|
| [insilico_exercise_ageing](https://github.com/cgjuan01/insilico_exercise_ageing) | In silico perturbation framework (Studies 2–3): contrastive pretraining, MR-informed refinement, PPR diffusion, ageing clock evaluation |
| [MR-GAT](https://github.com/cgjuan01) | Supervised graph attention network (Study 2): MR integration, GAT architecture, ablation testing |

---

## Publications

**Peer-reviewed**
- Juan CG, Matchett KB, Davison GW. A systematic review and meta-analysis of the SIRT1 response to exercise. *Sci Rep.* 2023;13:14752. https://doi.org/10.1038/s41598-023-38843-x
- Juan CG, Matchett KB, Davison GW. Exercise and nutrition: metabolic partners in epigenetic regulation. In: *Molecular Mechanisms in Nutritional Epigenetics.* Springer; 2024. https://doi.org/10.1007/978-3-031-54215-2_9

**Preprints**
- Juan CG, Ntasis L, et al. Multi-omic deep learning identifies exercise-responsive ageing pathways in humans. *medRxiv.* 2026. https://doi.org/10.64898/2025.12.26.25343061
- Juan CG, Ntasis L, et al. In silico network perturbation reveals hierarchical roles of DNA repair and glycosylation linking exercise to human ageing clocks. *medRxiv.* 2026. https://doi.org/10.64898/2026.02.01.26345311
- Juan CG, Šimunić-Briški N, et al. Quercetin activates the SIRT6–NRF2 axis during oxidative stress, modulating DNA repair and ageing-associated markers in healthy men. *medRxiv.* 2025. https://doi.org/10.1101/2025.10.31.25338366

---

## Citation

```bibtex
@phdthesis{juan2026causal,
  title   = {Causal Multi-Omic Deep Learning Reveals Genome Maintenance
             Programmes Linking Exercise to Biological Ageing in Humans},
  author  = {Juan, Ciara G.},
  school  = {Ulster University},
  year    = {2026},
  address = {Belfast, United Kingdom}
}
```

---

*PhD thesis submitted April 2026 · All rights reserved*
