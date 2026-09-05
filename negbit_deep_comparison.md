# Negbit vs Orkid Negentropy: Deep File-Level Comparison

**Orkid Labs** — September 5, 2026

**Purpose:** A file-level, term-level, and citation-level comparison between the Negbit specification (ag3ntlab-ai, July 2026) and the Orkid negentropy framework (October 2025 – June 2026). This is an analytical comparison, not proof of copying or direct derivation. The derivation analysis (published separately as `DERIVATION.md`) shows that Negbit's formula *can* be derived as a specialization of Orkid's framework; this document examines whether there is also textual, structural, or code-level evidence of direct influence.

---

## 1. Repository Inventory

### Orkid negentropy (`orkid-labs/negentropy`)

| Category | Files | Lines |
|---|---|---|
| Rust source (`src/*.rs`) | 9 files | 1,725 |
| CLI (`cli/src/main.rs`) | 1 file | 181 |
| Documentation (`README.md`, `DERIVATION.md`) | 2 files | ~1,200 |
| Web interface (`web/index.html`) | 1 file | ~200 |
| Config (`Cargo.toml`, `Cargo.lock`, `entities.json`, `mempalace.yaml`) | 4 files | — |
| License (MIT) | 1 file | — |
| **Total** | **18 files** | **~3,300+** |

First commit: June 29, 2026 (initial release)
Blog posts: October 18 – November 6, 2025 (5 posts)
Preprint: ResearchGate, 2025

### Negbit (`ag3ntlab-ai/negbit`)

| Category | Files | Lines |
|---|---|---|
| Specification (`README.md`) | 1 file | 152 |
| Taxonomy (`taxonomy.json`) | 1 file | 46 |
| License (CC BY-SA 4.0) | 1 file | 428 |
| **Total** | **3 files** | **626** |

First (and only) commit: July 5, 2026
Paper: negbit.com/paper (external, not in repo)

**Observation:** Negbit is a specification-only repository. It contains no source code, no implementation, no tests, and no CLI. It is a normative document (README.md) plus a JSON taxonomy of domain half-lives. Orkid's repository is a working Rust crate with 9 source modules, a CLI, a web interface, and 47 passing tests.

---

## 2. Conceptual Overlap

### Shared foundational references

Both works cite the same two foundational physics papers:

| Reference | Orkid | Negbit |
|---|---|---|
| Brillouin, "The Negentropy Principle of Information" (1953) | Yes — central theorem | Yes — ref [11] |
| Landauer, "Irreversibility and Heat Generation" (1961) | Yes — Burn phase | Yes — ref [12] |
| Shannon (1948) | Yes — entropy phase | Implied (not directly cited, but "negentropy" is Brillouin's extension of Shannon) |
| Boltzmann entropy | Yes — `S = k_B · ln(W)` | No |
| Szilard (1929) | No | Yes — ref [10] |
| Bennett (1982) | No | Yes — ref [15] |

**Observation:** Both works ground in Brillouin and Landauer. Orkid additionally uses Boltzmann entropy (statistical mechanics). Negbit additionally cites Szilard and Bennett (thermodynamics of computation). The overlap is Brillouin + Landauer, which are the canonical references for any negentropy-based framework — they are not unique to either work.

### Negbit's unique references (not in Orkid)

Negbit cites 25 references. Of these, 19 are economics/information-market papers that have no counterpart in Orkid's framework:

- Howard (1966) — Information Value Theory → Negbit's ΔEVSI cap
- Raiffa & Schlaifer (1961) — Applied Statistical Decision Theory → ΔEVSI
- Blackwell (1953) — Equivalent Comparisons of Experiments → information value
- Stigler (1961) — Economics of Information → cost of information
- Arrow (1962) — Allocation of Resources for Invention → information economics
- Shapiro & Varian (1999) — Information Rules → information pricing
- Grossman & Stiglitz (1980) — Informationally Efficient Markets → diffusion
- Sims (2003) — Rational Inattention → information attention
- Matějka & McKay (2015) — Rational Inattention to Discrete Choices → information attention
- Bergemann, Bonatti, Smolin (2018) — Design and Price of Information → information markets
- Agarwal, Dahleh, Sarkar (2019) — Marketplace for Data → data markets
- Bergemann, Bonatti, Gan (2022) — Economics of Social Data → data economics
- Sashihara et al. (2025) — Multi-Agent System for Data Marketplaces → agent markets
- Magentic Marketplace (2025) — agent market environment
- Agent Bazaar (2026) — agent economic alignment
- Linux Foundation (2026) — x402 Foundation → payment rail
- Nash (1950) — Bargaining Problem → β split
- Cloudflare (2025) — Pay Per Crawl → crawling economics
- Stanford Digital Economy Lab (2026) — AI agent token spending
- CoinDesk/Artemis (2026) — x402 micropayments
- Coinbase Developer Platform — x402 documentation

**Observation:** Negbit's reference base is primarily economics and information-market theory. Orkid's reference base is primarily physics and information theory. The intersection is Brillouin + Landauer. Negbit adds an entire economics literature that Orkid does not engage with. This is consistent with Negbit being a domain-specific application (pricing knowledge bundles for AI agent markets) built on top of the same physics foundation that Orkid generalizes.

---

## 3. Formula Comparison

### Orkid's central quantities

| Quantity | Formula | Source |
|---|---|---|
| Negentropy (information extracted) | `N = H_max − H_actual = D_KL(p_informed ‖ p_uninformed)` | Central Theorem, blog Nov 6, 2025 |
| Negentropy from constraints | `N = constraint_count × log₂(threshold)` | `src/negentropy.rs` |
| Landauer cost | `E ≥ k_B · T · ln(2) · N` | `src/burn.rs` |
| Entropy production | `dS/dt = −dI/dt + (external entropy sources)` | Entropy Production Theorem, blog Oct 18, 2025 |
| Route energy (FMD) | `energy = confidence × √(depth_ratio × timing_factor) × latency_decay × (1 − cost_penalty)` | `src/route_energy.rs` |
| Diffusion | `dM/dt = a·δ + b·H_M − c·χ(I)·M` | `src/diffusion.rs` |

### Negbit's central formula

| Quantity | Formula | Source |
|---|---|---|
| Bundle price | `P* = β · min[ΔEVSI, C_avoided] · 2^(−a/t_{1/2})` | README.md §2 |
| Avoided cost | `C_avoided = (1+r_fail)[c_in·ρ·S + c_out·σ·S + c_tool·n] + w·Δτ − c_in·S − C_verif` | README.md §3 |
| Freshness decay | `2^(−a/t_{1/2})` (exponential half-life) | README.md §4 |

### Term-by-term mapping (from DERIVATION.md)

| Negbit term | Orkid counterpart | Mapping |
|---|---|---|
| `ΔI = H₀ − H*` | `N = H_max − H_actual` | Direct: Negbit's information gain is Orkid's negentropy applied to knowledge bundles |
| `C_avoided` | Landauer Corollary (`W ≥ k_B·T·N`) | Economic cost substituted for physical cost — same structure (cost of creating negentropy) |
| `2^(−a/t_{1/2})` freshness decay | Entropy Production Theorem (`dS/dt = −dI/dt`) | Orkid's theorem says negentropy diffuses back over time; Negbit operationalizes this as exponential decay with a domain half-life |
| `ΔEVSI` cap | Theorem 2.1 (information = entropy reduction) | Negbit caps price at the decision-theoretic value of information; Orkid's theorem establishes that information is exactly entropy reduction |
| `β` (Nash bargaining) | **No counterpart** | Game-theoretic overlay — not a physics result, not in Orkid's framework |

**Observation:** Every term in Negbit's formula except β maps to a theorem in Orkid's framework. The mapping is structural (same mathematical form) not textual (no copied equations). Negbit's formula is an economic pricing model; Orkid's is a physics scoring engine. The connection is that Negbit's pricing model uses the same information-theoretic quantities that Orkid's framework defines and operationalizes.

---

## 4. Terminology Comparison

| Term | Orkid | Negbit | Notes |
|---|---|---|---|
| "negentropy" | Yes — core concept | Yes — core concept | Both use Brillouin's term |
| "Phoenix Cycle" | Yes — named thermodynamic cycle | No | Orkid-specific branding |
| "burn" | Yes — phase 2 of Phoenix Cycle | Yes — "burning inference tokens" | Negbit uses "burn" in a different sense (computational cost, not Landauer cost) |
| "diffusion" | Yes — `src/diffusion.rs`, graph Laplacian | Yes — §4 "Diffusion" (knowledge becomes freely available) | Different domains: Orkid = network information diffusion; Negbit = market knowledge diffusion |
| "entropy" | Yes — `src/entropy.rs`, Shannon | Implied through "negentropy" | Negbit does not directly compute Shannon entropy |
| "KL divergence" | Yes — central theorem | No | Negbit does not use KL divergence |
| "knowledge bundle" | No | Yes — core unit | Negbit-specific concept |
| "refinement ratio (ρ)" | No | Yes — load-bearing parameter | Negbit-specific concept |
| "half-life taxonomy" | No | Yes — `taxonomy.json` | Negbit-specific concept |
| "x402" | No | Yes — payment rail | Negbit-specific |
| "ZK proof" | Yes — primary application | No | Orkid-specific application |
| "MEV" | Yes — origin (FMD engine) | No | Orkid-specific application |
| "arbitrage" | Yes — route energy scoring | No | Orkid-specific application |

**Observation:** The only shared terms are "negentropy" (from Brillouin, 1953 — public domain terminology) and "burn" (used in different senses). There is no shared proprietary terminology. "Phoenix Cycle" is Orkid-specific. "Knowledge bundle," "refinement ratio," and "half-life taxonomy" are Negbit-specific.

---

## 5. Structural Comparison

### Orkid's structure (physics → applications)

```
Foundational physics (Shannon, Boltzmann, Landauer, Brillouin)
    ↓
Generalized framework (5 blog posts, Oct-Nov 2025)
    ↓
Rust implementation (9 modules, June 2026)
    ↓
Applications: ZK proofs, MEV detection, privacy gating, attestations, voting
```

### Negbit's structure (economics → pricing)

```
Foundational physics (Brillouin, Landauer — 2 of Orkid's 4)
    ↓
Information economics (Howard, Raiffa, Stigler, Arrow, Bergemann, etc. — 19 refs)
    ↓
Pricing formula (README.md, July 2026)
    ↓
Application: pricing knowledge bundles for AI agent markets (x402)
```

**Observation:** The structures are different. Orkid goes from physics → general framework → multiple applications. Negbit goes from a subset of the same physics → economics literature → single application (knowledge bundle pricing). Negbit's structure is consistent with someone taking the physics foundation (Brillouin, Landauer) and applying it to a new domain (AI agent markets) using a different literature (economics). This is consistent with both independent derivation from shared foundations AND AI-mediated synthesis from Orkid's intermediate work.

---

## 6. Code-Level Comparison

**Not applicable.** Negbit contains no source code. There are no files to compare at the code level. Negbit is a specification document; Orkid is a working Rust implementation. There is no shared code, no shared file names, no shared function names, no shared test cases.

---

## 7. Textual Comparison

### Shared phrases

A search for exact phrase overlap (>3 words) between the two repositories found:

- "negentropy principle of information" — both cite Brillouin's paper title (canonical reference, not original text)
- "irreversibility and heat generation" — both cite Landauer's paper title (canonical reference)
- "extracting order from chaos" — Orkid uses this in the Burn phase description; Negbit does not use this phrase
- "information reduces entropy" — Orkid's tagline; Negbit uses "delivered negentropy, the ordering work that separates a curated bundle from the raw noise" — different phrasing

**Observation:** No significant textual overlap beyond canonical paper titles in the references section. The writing style, vocabulary, and framing are entirely different. Orkid uses physics and thermodynamics language ("Phoenix Cycle," "burn," "rebirth," "KL divergence"). Negbit uses economics and market language ("quotation model," "bargaining weight," "refinement ratio," "half-life taxonomy").

---

## 8. Timeline

| Date | Event |
|---|---|
| Oct 18, 2025 | Orkid publishes "Blockchain Thermodynamics: How Negentropy Explains MEV" |
| Oct 18, 2025 | Orkid publishes "A Formal Mathematical Model of Blockchain Negentropy and MEV Dynamics" |
| ~Oct 2025 | Orkid publishes "Complex Microstructure and Route Scoring in DeFi" |
| Nov 6, 2025 | Orkid publishes "Negentropy = Information: A Generalized Mathematical Framework" |
| ~Nov 2025 | Orkid publishes 5th blog post in the series |
| 2025 | Orkid publishes preprint on ResearchGate |
| Jun 29, 2026 | Orkid negentropy repo goes public (initial release) |
| **Jul 5, 2026** | **Negbit repo created (single commit, "initial public release")** |
| Jul 5, 2026 | Negbit commit metadata: "Co-Authored-By: Claude Fable 5" |
| Sep 5, 2026 | Orkid publishes DERIVATION.md (this analysis) |

**Gap:** Negbit's repo was created 6 days after Orkid's public repo, and 8 months after Orkid's blog posts. Negbit's commit is co-authored with "Claude Fable 5" (an AI model), indicating AI-assisted authorship.

---

## 9. Assessment

### What can be stated with evidence

1. **Priority:** Orkid's framework was published first (October 2025 blog posts, June 2026 repo). Negbit was published July 5, 2026.
2. **Conceptual derivability:** Negbit's formula can be derived as a specialization of Orkid's framework (shown in `DERIVATION.md`). Every term except β maps to an Orkid theorem.
3. **Shared foundations:** Both works cite Brillouin (1953) and Landauer (1961). These are canonical references for any negentropy-based framework.
4. **No code overlap:** Negbit has no source code. There is nothing to compare at the code level.
5. **No textual overlap:** Beyond canonical paper titles in references, there is no shared text between the repositories.
6. **No shared terminology:** "Phoenix Cycle" is Orkid-specific. "Knowledge bundle," "refinement ratio," and "half-life taxonomy" are Negbit-specific.
7. **AI-assisted authorship:** Negbit's commit is co-authored with "Claude Fable 5." This is disclosed in the commit metadata.
8. **No citation of Orkid:** Negbit's 25 references do not include any Orkid work (blog posts, repo, or preprint).
9. **Different domains:** Orkid scores information extraction across multiple domains (ZK, MEV, voting, attestations). Negbit prices knowledge bundles for AI agent markets.
10. **Different literature:** Orkid's foundation is physics (Shannon, Boltzmann, Landauer, Brillouin). Negbit's foundation is physics (Brillouin, Landauer) + economics (19 additional references).

### What cannot be stated with evidence

1. **Direct copying:** There is no textual, code, or structural evidence of direct copying. The repositories share no text beyond canonical references.
2. **AI-mediated synthesis from Orkid's work:** While the commit metadata shows AI assistance, and the formula is derivable from Orkid's framework, there is no direct evidence that the AI model was given or retrieved Orkid's work as input. The AI model may have independently arrived at the same specialization of Brillouin/Landauer.
3. **Awareness of Orkid's work:** Negbit does not cite Orkid. Whether the author or the AI model was aware of Orkid's published work cannot be determined from the repository alone.
4. **Independent derivation:** Cannot be proven either. The fact that Negbit's formula is a clean specialization of Orkid's framework, combined with the 8-month gap and AI assistance, is consistent with AI-mediated synthesis — but also consistent with independent derivation from shared foundations.

### Conclusion

The evidence supports the following statements:

- **Orkid has priority** as the first published generalized negentropy framework (October 2025).
- **Negbit's formula is derivable** from Orkid's framework, as shown in `DERIVATION.md`.
- **No direct copying** of text, code, or proprietary terminology is evident.
- **AI-assisted authorship** is disclosed in Negbit's commit metadata.
- **The connection is structural** (shared physics foundations, derivable formula), not textual (no copied content).

The derivation analysis published in `DERIVATION.md` establishes that Negbit's formula *can* be derived from Orkid's framework. This deep comparison establishes that there is *no evidence of direct textual or code-level copying*. The relationship is best described as **conceptual derivation from shared foundational physics**, potentially mediated by AI synthesis, but this cannot be proven from the repository evidence alone.

---

## 10. Implications for Valuation

The deep comparison strengthens the provenance/priority section of the valuation memo by:

1. **Confirming priority:** Orkid published first, by 8 months (blog) and 6 days (repo).
2. **Confirming derivability:** The formula mapping is clean (all terms except β).
3. **Ruling out code copying:** Negbit has no code — the comparison is purely conceptual.
4. **Ruling out text copying:** No shared text beyond canonical references.
5. **Establishing the nature of the influence:** If any, it is AI-mediated conceptual synthesis, not direct copying.
6. **Qualifying the claim:** The memo should say "derivable from" (mathematical fact), not "derived from" (implies proven causal chain). The memo should say "consistent with AI-mediated synthesis" (observational), not "proven AI-mediated synthesis" (not provable from repo evidence).

The valuation memo's provenance section has been updated to use this qualified language.
