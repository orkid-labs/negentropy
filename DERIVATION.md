# Mathematical Mapping: Negbit Pricing and the Orkid Negentropy Framework

**Orkid Labs** — September 2026

**Citing:**
- Repository: [github.com/orkid-labs/negentropy](https://github.com/orkid-labs/negentropy) — "The physics of information extraction — open-source thermodynamic engine for scoring any system where information reduces entropy" (1,725 lines Rust, MIT licensed, created June 30, 2026)
- Framework post: [orkidlabs.com/blog/negentropy-information-generalized-framework](https://www.orkidlabs.com/blog/negentropy-information-generalized-framework/) — "Negentropy = Information: A Generalized Mathematical Framework" (published November 6, 2025)
- Blockchain thermodynamics: [orkidlabs.com/blog/blockchain-thermodynamics-negentropy-mev-physics](https://www.orkidlabs.com/blog/blockchain-thermodynamics-negentropy-mev-physics/) (published October 18, 2025)
- Formal model: [orkidlabs.com/blog/formal-negentropy-model-mev-dynamics-graph-diffusion](https://www.orkidlabs.com/blog/formal-negentropy-model-mev-dynamics-graph-diffusion/) (published October 18, 2025)
- Preprint: Jacob Cavazos, "Negative EV per Unit Time as Blockchain Inefficiency," ResearchGate (2025)

---

## Abstract

We show that the Negbit quotation model for AI agent knowledge bundles (Limare, ag3ntlab, July 2026) is mathematically mappable to the generalized negentropy framework published by Orkid Labs in October–November 2025: every term in the Negbit formula except the Nash bargaining split (β) corresponds to a theorem in the Orkid framework. However, Negbit's paper also contains its own complete, independently-cited derivation path through economics literature (Stigler, Sims, Grossman-Stiglitz, Howard, Raiffa, Nash), not through Orkid's physics framework. The mathematical mapping is valid as a structural observation, but it does not establish a causal derivation chain. The correct framing is that both works independently specialize the same foundational physics (Shannon, Brillouin, Landauer) into different domains through different intermediate literatures. We discuss the implications for priority and the distinction between mathematical mappability and causal derivation.

---

## 1. The Generalized Framework (Orkid Labs, October–November 2025)

Orkid Labs published a generalized mathematical framework unifying Shannon information theory, Boltzmann statistical mechanics, Landauer's principle, and Brillouin's negentropy principle into a single scoring engine. The framework was published in five blog posts between October 18 and November 6, 2025, with a production Rust implementation released as an open-source repository on June 30, 2026.

### 1.1 Central Theorem

**Theorem (Negentropy = Information):** For any system with prior $p_{\text{prior}}$ and posterior $p_{\text{posterior}}$:

$$\text{Neg}(p_{\text{posterior}}) = I(D) = D_{\text{KL}}(p_{\text{posterior}} \| p_{\text{prior}})$$

where $D_{\text{KL}}$ is the Kullback-Leibler divergence.

*Proof:* $\text{Neg}(p_{\text{post}}) = H_{\max} - H(p_{\text{post}}) = H(p_{\text{prior}}) - H(p_{\text{post}}) + [H_{\max} - H(p_{\text{prior}})] = I(D) + \text{Neg}(p_{\text{prior}})$. Measuring negentropy relative to the prior yields exactly the information. $\square$

**Source:** [Orkid Labs, "Negentropy = Information: A Generalized Mathematical Framework," §2.4, Theorem 2.2](https://www.orkidlabs.com/blog/negentropy-information-generalized-framework/), published November 6, 2025.

### 1.2 Landauer Corollary

**Corollary (Cost of Information):** Creating negentropy (reducing entropy) requires work:

$$W \geq k_B \cdot T \cdot \text{Neg}$$

*Source:* Same framework, §5.2, Corollary 5.1. This is Landauer's principle (1961) generalized: the minimum energy to create $N$ bits of negentropy is $k_B T \ln 2 \cdot N$.

### 1.3 Entropy Production Theorem

**Theorem (Coupled Dynamics):** In any system where information $I(t)$ evolves:

$$\frac{dS}{dt} = -\frac{dI}{dt} + \text{(external entropy sources)}$$

The rate of entropy decrease equals the rate of information increase. Negentropy extracted at $t=0$ diffuses back into the system as information becomes public.

*Source:* Same framework, §5.1, Theorem 5.1.

### 1.4 The Phoenix Cycle

The framework operationalizes these theorems into a thermodynamic cycle that any information extraction passes through:

```
ENTROPY (chaos) → BURN (energy) → EXTRACTION (negentropy) → REBIRTH (order)
```

1. **Entropy:** High-entropy state (uncertainty, private data, market inefficiency)
2. **Burn:** Landauer cost paid to extract order from chaos
3. **Extraction:** Negentropy pulled from the ashes ($N = \text{constraint\_count} \times \log_2(\text{threshold})$)
4. **Rebirth:** Verifiable artifact produced (ZK proof, settled arbitrage, anonymous vote)

*Source:* [github.com/orkid-labs/negentropy](https://github.com/orkid-labs/negentropy), README.md, production Rust implementation.

### 1.5 Production Deployment

The framework is not theoretical. It is a production dependency in six public repositories:

| Repository | Application | Negentropy score |
|---|---|---|
| `orkid-labs/zk-age` | Age verification (Groth16 ZK proofs) | $N = 17 \times \log_2(18) \approx 70.9$ bits |
| `orkid-labs/zk-attest` | Attestations on Hedera | Attestation energy model from FMD physics |
| `orkid-labs/zenkinetic` | Privacy gate for Horizen L3 | Negentropy-scored confidential transactions |
| `orkid-labs/horizen-age` | Age verification on Horizen L3 | ZK proofs scored by negentropy |
| `orkid-labs/horizen-attest` | Attestations on Horizen L3 | ZK proofs scored by negentropy |
| `orkid-labs/horizen-ballot` | Voting on Horizen L3 | Halo2 ZK proofs scored by negentropy |

The engine was generalized from the Orkid FMD (Financial Molecular Dynamics) physics engine — a production MEV detection system that treats market inefficiency as thermodynamic negentropy.

---

## 2. The Domain-Specific Formula (Negbit, July 2026)

In July 2026, ag3ntlab-ai published <a href="https://negbit.com/paper" rel="nofollow">"Pricing Negentropy: A Quotation Model for Pre-Processed Context Bundles in Machine-to-Machine Knowledge Markets"</a> (Nicolas Limare, ag3ntlab, v1.0, July 2026). The repository was created on GitHub on July 5, 2026 — five days after the Orkid negentropy repository was made public, and eight months after Orkid's framework blog posts were published.

The Negbit formula prices a knowledge bundle of $S$ tokens, age $a$ days, in a domain with half-life $t_{1/2}$:

$$P^* = \beta \cdot \min[\Delta\text{EVSI},\; C_{\text{avoided}}] \cdot 2^{-a/t_{1/2}}$$

with terms:

| Symbol | Meaning |
|---|---|
| $C_{\text{avoided}}$ | Processing cost the buyer skips by taking the bundle |
| $\Delta\text{EVSI}$ | Decision-theoretic value of the information (expected value of sample information) |
| $\beta$ | Bargaining weight (seller's share of surplus) |
| $2^{-a/t_{1/2}}$ | Freshness decay — value halves every domain half-life |

The avoided cost expands to:

$$C_{\text{avoided}} = (1 + r_{\text{fail}}) \cdot [c_{\text{in}} \cdot \rho \cdot S + c_{\text{out}} \cdot \sigma \cdot S + c_{\text{tool}} \cdot n] + w \cdot \Delta\tau$$

where $\rho = d_B / d_{\text{raw}}$ is the refinement ratio (bundle bit density vs raw source bit density).

---

## 3. Derivation: Negbit from Orkid

We now derive every term in the Negbit formula from the Orkid framework.

### Step 1: Negentropy of a knowledge bundle

**Orkid Central Theorem:** $\text{Neg} = H_{\max} - H_{\text{actual}} = \Delta I$

A knowledge bundle is an information extraction — it takes raw, high-entropy sources and produces a curated, lower-entropy artifact. Applying Orkid's Central Theorem:

$$N_{\text{bundle}} = H_{\text{raw}} - H_{\text{bundle}} = \Delta I = H_0 - H^*$$

**This is Negbit's $\Delta I = H_0 - H^*$.** Negbit's information gap is Orkid's negentropy applied to knowledge curation. Same operation, specific domain.

### Step 2: The refinement ratio is a negentropy density

Negbit defines $d_{\text{raw}}$ (bits per token in raw sources) and $d_B$ (bits per token in bundle), with $\rho = d_B / d_{\text{raw}}$.

In Orkid's framework, the negentropy of a bundle of $S$ tokens is:

$$N = d_B \cdot S \quad \text{(total negentropy delivered)}$$

The same negentropy from raw sources requires:

$$N = d_{\text{raw}} \cdot (\rho \cdot S) = d_B \cdot S \quad \text{(same negentropy, } \rho \times \text{more tokens)}$$

The refinement ratio $\rho$ is the **negentropy concentration factor** — how much the bundle compresses negentropy relative to raw sources. This is a direct consequence of Orkid's framework: the bundle is a negentropy concentration mechanism.

### Step 3: Landauer cost → economic cost substitution

**Orkid Landauer Corollary:** $W \geq k_B \cdot T \cdot N$

Negbit makes the identical substitution at the economic scale. Instead of physical energy ($k_B \cdot T$), use the economic cost of processing one bit from raw sources:

$$\text{cost\_per\_bit}_{\text{raw}} = \frac{c_{\text{in}}}{d_{\text{raw}}} \quad \text{(dollars per token } \div \text{ bits per token = dollars per bit)}$$

So the economic cost of extracting $N$ bits of negentropy from raw sources:

$$C \geq \frac{c_{\text{in}}}{d_{\text{raw}}} \cdot N \quad \text{(economic Landauer bound)}$$

**This is Negbit's "economic Landauer gap" (§5.3).** Negbit explicitly names this substitution: "the economic cost of extracting one useful bit from the raw web with 2026 LLMs exceeds the physical floor by roughly twenty-five orders of magnitude." That gap is Orkid's Landauer corollary with the economic cost function substituted for the physical one.

### Step 4: The avoided cost is negentropy × cost per bit

Negbit's avoided cost (dominant term):

$$C_{\text{avoided}} \approx c_{\text{in}} \cdot \rho \cdot S$$

Substituting $\rho = d_B / d_{\text{raw}}$ and $N = d_B \cdot S$:

$$c_{\text{in}} \cdot \rho \cdot S = c_{\text{in}} \cdot \frac{d_B}{d_{\text{raw}}} \cdot S = \frac{c_{\text{in}}}{d_{\text{raw}}} \cdot (d_B \cdot S) = \text{cost\_per\_bit}_{\text{raw}} \cdot N_{\text{bundle}}$$

**Negbit's avoided cost is Orkid's negentropy score multiplied by the economic cost per bit.** The price is the negentropy score denominated in dollars instead of bits.

### Step 5: The value cap is decision-relevant negentropy

Negbit's $\Delta\text{EVSI}$ caps the price. In Orkid's framework, this is the negentropy of the information relative to the buyer's decision — how much does this information reduce the buyer's uncertainty about which action to take?

**Orkid Theorem 2.1:** $I(D) = H(p_{\text{prior}}) - H(p_{\text{posterior}}) \geq 0$

Negbit's $\Delta\text{EVSI}$ is this same quantity, bounded by the decision context (the information is only valuable if it changes the optimal action — Blackwell's ordering [3]). The value cap is Orkid's information-as-entropy-reduction applied to decision theory.

### Step 6: The freshness decay is negentropy diffusion

Negbit's $2^{-a/t_{1/2}}$ decay represents information diffusion — as information becomes public, its negentropy content decreases (the gap between informed and uninformed distributions shrinks).

**Orkid Entropy Production Theorem:** $\frac{dS}{dt} = -\frac{dI}{dt} + \text{(external entropy sources)}$

Negentropy extracted at $t=0$ diffuses back into the system as the information becomes public. The half-life $t_{1/2}$ is the time constant of this diffusion. **Negbit's freshness decay is Orkid's entropy production theorem applied to information markets.**

### Step 7: Assemble the formula

Starting from Orkid's framework:

1. $N = H_{\text{raw}} - H_{\text{bundle}} = \Delta I$ — negentropy of the bundle [Orkid Central Theorem]
2. $N = d_B \cdot S$ — negentropy in terms of bundle density and size [Step 2]
3. $C \geq \frac{c_{\text{in}}}{d_{\text{raw}}} \cdot N$ — economic cost of extracting $N$ bits [Orkid Landauer, economic substitution]
4. $C_{\text{avoided}} \approx \text{cost\_per\_bit}_{\text{raw}} \cdot N = c_{\text{in}} \cdot \rho \cdot S$ — buyer's avoided cost [Step 4]
5. $\Delta\text{EVSI}$ — decision-relevant negentropy cap [Orkid Theorem 2.1 + Blackwell]
6. $N(t) = N(0) \cdot 2^{-t/t_{1/2}}$ — negentropy diffusion [Orkid Entropy Production Theorem]
7. $P = \beta \cdot \min[\Delta\text{EVSI}, C_{\text{avoided}}] \cdot 2^{-a/t_{1/2}}$ — price = negentropy score × cost per bit, capped, decayed, split

**This is Negbit's equation (5), derived from Orkid's framework.**

---

## 4. Term-by-Term Mapping

| Negbit term | Orkid source | Derivation |
|---|---|---|
| $\Delta I = H_0 - H^*$ | Central Theorem: $N = H_{\max} - H_{\text{actual}}$ | Direct application to knowledge bundles |
| $\rho = d_B/d_{\text{raw}}$ | Negentropy density: $N = d_B \cdot S$ | Ratio of bundle density to raw density |
| $C_{\text{avoided}}$ | Landauer Corollary: $W \geq k_B \cdot T \cdot N$ | Substitute economic cost ($c_{\text{in}}/d_{\text{raw}}$) for physical cost ($k_B \cdot T$) |
| $\Delta\text{EVSI}$ cap | Theorem 2.1: $I(D) = H(\text{prior}) - H(\text{posterior})$ | Decision-relevant negentropy bound |
| $2^{-a/t_{1/2}}$ decay | Theorem 5.1: $dS/dt = -dI/dt + \text{sources}$ | Negentropy diffusion (second law) |
| $\beta$ bargaining split | **Not in Orkid framework** | Nash bargaining overlay (game theory, not physics) |

**Every term in the Negbit formula except $\beta$ maps directly to a theorem in Orkid's published framework.** $\beta$ is a Nash bargaining split [Negbit ref 21] for dividing the negentropy surplus between buyer and seller — a game-theoretic overlay on top of the physics, not a replacement for it.

---

## 5. The Direction of Derivation

The general → specific direction works. The specific → general direction does not.

**You can derive Negbit from Orkid:** Take the generalized negentropy scoring framework, restrict the domain to knowledge bundles, substitute economic cost for physical cost, add a Nash bargaining split. The derivation is mechanical (§3).

**You cannot derive Orkid from Negbit:** Negbit has no notion of ZK proofs, MEV detection, privacy gating, Boltzmann entropy, the Phoenix Cycle, or scoring cryptographic work. It is a single-domain pricing formula. Generalizing it to Orkid's framework would require inventing the unification of Shannon + Boltzmann + Landauer + Brillouin, the Phoenix Cycle operationalization, and the cross-domain scoring engine — none of which are present in Negbit.

---

## 6. Timeline and Provenance

| Date | Event |
|---|---|
| October 18, 2025 | Orkid publishes "Blockchain Thermodynamics: How Negentropy Explains MEV, Consensus, and Arbitrage" |
| October 18, 2025 | Orkid publishes "A Formal Mathematical Model of Blockchain Negentropy and MEV Dynamics" |
| October 18, 2025 | Orkid publishes "Negative EV Rate as Blockchain Inefficiency" |
| November 6, 2025 | Orkid publishes "Negentropy = Information: A Generalized Mathematical Framework" |
| November 6, 2025 | Orkid publishes "The Thermodynamic Balance of Global Networks" |
| June 30, 2026 | Orkid publishes negentropy Rust repo at github.com/orkid-labs/negentropy |
| **July 5, 2026** | **Negbit repo created at <a href="https://github.com/ag3ntlab-ai/negbit" rel="nofollow">github.com/ag3ntlab-ai/negbit</a> (5 days after Orkid's repo, 8 months after Orkid's blog posts)** |
| July 5, 2026 | Negbit paper published (v1.0, July 2026) |

The Negbit paper's reference section cites 25 sources, including Brillouin [11], Landauer [12], Shannon (via Sims [8]), and Bennett [15] — the same foundational principles Orkid's framework unifies. The paper does not cite any of Orkid's five published blog posts, the ResearchGate preprint, or the public GitHub repository.

The Negbit repository's single commit message reads: "spec: The Negbit Spec v1.0 — initial public release [...] Co-Authored-By: Claude Fable 5."

---

## 7. Negbit's Own Derivation Path

**Critical context:** Negbit's paper (negbit.com/paper) contains a complete, independently-cited derivation of its formula through **economics literature**, not through Orkid's physics framework. The paper does not merely state the formula — it derives it step by step:

| Step | Negbit's derivation | Cited source |
|---|---|---|
| §3.1: Information density | `ΔI = H₀ − H*` — standard information theory | Shannon (via standard notation) |
| §3.2: Make-or-buy | `P_max` from buyer's DIY cost vs buying | Stigler (1961), Shapiro & Varian (1999) |
| §3.3: Info-theoretic skeleton | `c_in · ΔI · (1/d_raw − 1/d_B)` from rational inattention | Sims (2003) — "the buyer's λ is its metered processing cost" |
| §3.4: Value cap | `ΔEVSI` cap | Howard (1966), Raiffa & Schlaifer (1961), Bergemann et al. (2018) |
| §3.5: Temporal decay | `2^(−t/t½)` from information diffusion | Grossman & Stiglitz (1980) — "the mechanism behind our decay term" |
| §3.7: Bargaining | `β · P_ceiling` | Nash (1950) |

Negbit's paper explicitly states about Brillouin and Landauer: **"We use this only to locate the market"** — the thermodynamic references establish the gap between physical cost (~10⁻²⁹ dollars) and economic cost (~10⁻⁴ dollars), but the formula itself is derived from economics, not physics.

### What this means for the mapping

The mathematical mapping in §3–§4 of this document is valid: the formulas ARE structurally mappable. But the mapping should not be presented as a causal derivation chain (Negbit derived from Orkid) when:

1. Negbit has its own complete, cited derivation through economics literature
2. Negbit explicitly uses Brillouin/Landauer only as market context, not as the basis of its formula
3. The economics literature (Stigler, Sims, Grossman-Stiglitz, Howard, Raiffa) provides an independent path to the same formula structure

### On AI-assisted authorship

The commit metadata indicates AI assistance ("Co-Authored-By: Claude Fable 5"). This is consistent with several explanations:

1. **Independent AI-assisted derivation from economics:** The AI model derived the formula from the economics literature that Negbit cites, without accessing Orkid's work.
2. **AI-mediated synthesis from multiple sources including Orkid:** The AI model found Orkid's work via web search AND the economics literature, synthesizing from both.
3. **AI-assisted derivation from Orkid only:** The AI model found Orkid's work and specialized it, with the economics citations added as post-hoc justification.

The repository evidence cannot distinguish between these explanations. Negbit's complete economics-based derivation makes explanation (1) fully consistent with the evidence — the formula does not require Orkid's framework to derive. The 8-month gap after Orkid's blog posts makes explanation (2) possible but unprovable. Explanation (3) is the weakest given Negbit's complete cited derivation path.

We assert only that:
- The mathematical mapping is valid (§3–§4)
- The timeline is consistent with but does not prove influence (§6)
- The commit metadata indicates AI assistance (§6)
- Negbit has its own complete derivation path through economics literature (this section)

---

## 8. Implications

### 8.1 Orkid's framework is the generalized primitive; Negbit is one convergent specialization

Orkid's framework is the first published generalized negentropy scoring framework (October 2025). Negbit is a domain-specific pricing formula (July 2026) that is mathematically mappable to Orkid's framework but has its own independent derivation path through economics literature. Both works specialize the same foundational physics (Shannon, Brillouin, Landauer) into different domains through different intermediate literatures.

This is **convergent specialization**: two independent works applying the same foundational principles to different domains, producing mathematically mappable formulas through different derivation paths. Orkid's priority as the first published generalized framework is established by the publication record. Whether Negbit's formula was influenced by Orkid's published work during AI-assisted synthesis cannot be determined from the repository evidence — and it does not need to be. Priority is established by publication date, not by proving that later works derived from the earlier one.

### 8.2 The scoring primitive vs. the pricing application

Orkid's negentropy engine scores information extraction in **bits** — how much uncertainty did this ZK proof eliminate? How much negentropy did this arbitrage route extract? The score is the fundamental quantity.

Negbit prices knowledge bundles in **dollars** — what should you pay for this curated context? The price is the score denominated in a different unit (dollars instead of bits), converted via the economic cost per bit.

A price is a score in a different currency. Orkid's engine is the scoring primitive. Negbit is a pricing application. The primitive can power the application (convert bits to dollars via cost per bit). The application cannot power the primitive (it is domain-specific to knowledge bundles).

### 8.3 Production deployment as the differentiator

Orkid's negentropy engine is a production Rust crate deployed as a dependency in six public repositories, scoring real ZK proofs, gating real privacy transactions, and detecting real MEV. Negbit is a specification with a reference quoting tool. The framework that enables production systems is the framework that matters.

---

## References

1. Orkid Labs, "Negentropy = Information: A Generalized Mathematical Framework," orkidlabs.com/blog/negentropy-information-generalized-framework, November 6, 2025.
2. Orkid Labs, "Blockchain Thermodynamics: How Negentropy Explains MEV, Consensus, and Arbitrage," orkidlabs.com/blog/blockchain-thermodynamics-negentropy-mev-physics, October 18, 2025.
3. Orkid Labs, "A Formal Mathematical Model of Blockchain Negentropy and MEV Dynamics," orkidlabs.com/blog/formal-negentropy-model-mev-dynamics-graph-diffusion, October 18, 2025.
4. Orkid Labs, "Negative EV Rate as Blockchain Inefficiency: A Mathematical Framework for MEV," orkidlabs.com/blog/negative-ev-rate-blockchain-inefficiency, October 18, 2025.
5. Orkid Labs, "The Thermodynamic Balance of Global Networks," orkidlabs.com/blog/thermodynamic-balance-global-networks-comprehensive, November 6, 2025.
6. Orkid Labs, negentropy (Rust crate), github.com/orkid-labs/negentropy, MIT License, created June 30, 2026.
7. J. Cavazos, "Negative EV per Unit Time as Blockchain Inefficiency," ResearchGate preprint, 2025.
8. N. Limare, "Pricing Negentropy: A Quotation Model for Pre-Processed Context Bundles in Machine-to-Machine Knowledge Markets," ag3ntlab, v1.0, July 2026. <a href="https://negbit.com/paper" rel="nofollow">negbit.com/paper</a>
9. C. E. Shannon, "A Mathematical Theory of Communication," Bell System Technical Journal, 27(3), 379–423, 1948.
10. L. Boltzmann, "Über die Beziehung zwischen dem zweiten Hauptsatze der mechanischen Wärmetheorie und der Wahrscheinlichkeitsrechnung," Wiener Berichte, 76, 373–435, 1877.
11. R. Landauer, "Irreversibility and Heat Generation in the Computing Process," IBM Journal of Research and Development, 5(3), 183–191, 1961.
12. L. Brillouin, "Negentropy Principle of Information," Journal of Applied Physics, 24(9), 1152–1163, 1953.
13. S. Kullback, R. A. Leibler, "On Information and Sufficiency," Annals of Mathematical Statistics, 22(1), 79–86, 1951.
14. C. A. Sims, "Implications of Rational Inattention," Journal of Monetary Economics, 50(3), 665–690, 2003.
15. J. F. Nash, "The Bargaining Problem," Econometrica, 18(2), 155–162, 1950.

---

*Built by Orkid Labs — privacy-first crypto engineering. See the signal. Move with intent.*

*Repository: [github.com/orkid-labs/negentropy](https://github.com/orkid-labs/negentropy)*
*Website: [orkidlabs.com](https://www.orkidlabs.com)*
