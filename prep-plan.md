# 10-Week Prep Plan — Efficient Transformers & Theoretical KV Cache Compression

## Strategic framing

The stated north star — *provable guarantees* and *information-theoretic lower bounds on KV cache size* — is the right long-term direction, but as a solo researcher without an advisor, aiming straight at a hard theorem in 10 weeks risks producing nothing shippable. Theorems that survive review usually need a supervisor and months of iteration.

Comparative advantage: a strong systems/engineering background. In efficient-inference research the strongest independent contributions are **empirical-theoretical** — measure the real structure (rank, entropy, redundancy) of KV caches, then bound heuristics against it. This plays to that strength, is achievable alone, and produces artifacts PhD admissions committees can actually see.

**Goal for 10 weeks:** one reproducible open-source benchmark + one well-argued technical report / blog series, with the math foundation built *in service of* that artifact — not as an open-ended reading list.

---

## The plan

### Weeks 1–2 — Instrument & reproduce
- Pick one small open model runnable locally (e.g. Llama-3.2-1B / Qwen2.5-1.5B). Write clean hooks to **dump the full KV cache** per layer/head during generation on a long-context task (a few LongBench or RULER tasks).
- Reproduce **one** heuristic end-to-end from scratch — **H2O** or **SnapKV** (simplest, most cited). Match its reported eviction behavior.
- **Deliverable:** a repo that dumps caches + a faithful reimplementation with a plot matching the paper.

**Research questions:**
- *Week 1:* What does the KV cache actually contain — how do key/value magnitudes and attention mass distribute across layers, heads, and token positions during long-context generation?
- *Week 2:* Does a from-scratch reimplementation of the chosen heuristic reproduce the paper's reported quality-vs-budget curve, and where does it diverge?

### Weeks 3–4 — Measure the structure (the "theory" hook)
- Compute, per layer and head: singular-value spectra of the K and V matrices (how low-rank *is* the cache?), attention-weight entropy, and token-importance concentration. Answers the "low-rank / sparse structure" open question **empirically** first.
- Parallel math track: **numerical linear algebra** (SVD, low-rank approximation, Eckart–Young) — Trefethen & Bau lectures 1–5. Only what's needed to interpret the plots.
- **Deliverable:** "How compressible is the KV cache, really?" — a notebook + writeup with spectra across depth.

**Research questions:**
- *Week 3:* How low-rank is the KV cache in practice — what fraction of singular-value energy is captured by the top-k components, and how does that vary across layers and heads?
- *Week 4:* Is per-token importance concentrated (sparse) or diffuse, and does attention-weight entropy predict which tokens a good heuristic should keep?

### Weeks 5–6 — Build an oracle / upper bound
- Construct an **oracle compressor**: with full future knowledge, what is the smallest cache (tokens kept, or bits via quantization) that preserves output within tolerance ε? Empirical stand-in for a lower bound — the gap between heuristics and oracle is a real, novel measurement.
- Add **KIVI**-style quantization to the comparison to cover both eviction and quantization axes.
- Parallel math track: **information theory** — Cover & Thomas ch. 2 (entropy, mutual information), ch. 10 intro (rate–distortion). Frame the oracle as an empirical rate–distortion curve.

**Research questions:**
- *Week 5:* With full future knowledge, what is the minimum cache budget (tokens or bits) that preserves generation quality within tolerance ε — i.e., what does the oracle frontier look like?
- *Week 6:* Along which axis is the cache more compressible — eviction (fewer tokens) or quantization (fewer bits per token) — and how does the oracle trade the two off?

### Weeks 7–8 — Analyze & write the technical report
- Pull it together: for each method (H2O, SnapKV, KIVI, StreamingLLM), plot achieved quality vs. cache budget against the oracle frontier. Where do heuristics leave value on the table? Does the gap correlate with the measured rank/entropy structure?
- Write it as a proper short report (LaTeX, arXiv-style, 6–8 pages) **and** a readable blog post on the Hugo site. Blog post = public research signal; report = rigor.

**Research questions:**
- *Week 7:* How large is the gap between each heuristic (H2O, SnapKV, KIVI, StreamingLLM) and the oracle frontier, and which method is closest at each budget?
- *Week 8:* Does the heuristic–oracle gap correlate with the measured rank/entropy structure — i.e., do heuristics fail exactly where the cache is least compressible?

### Weeks 9–10 — Sharpen one contribution + de-risk PhD apps
- From the gaps found, propose **one** concrete, structure-aware improvement and prototype it. Even a modest, honest "structure-aware budget allocation beats uniform by X%" is a real result.
- Turn the three open questions into a **1-page research statement draft** grounded in the new data — the backbone of PhD applications.
- Cold-email 2–3 authors of the reproduced papers with the benchmark repo + a specific question. A working reproduction earns replies — the single highest-leverage move for landing an advisor.

**Research questions:**
- *Week 9:* Can a structure-aware rule (e.g., budget allocated by measured rank/entropy) close a measurable part of the heuristic–oracle gap versus uniform allocation?
- *Week 10:* Which of the three open questions is now best supported by evidence, and what is the sharpest single claim defensible in a research statement?

---

## Running throughout
- **Cadence:** ship a short blog post every ~2 weeks. Public artifacts compound.
- **Scope discipline:** one model, ≤2 tasks, 4 methods. Depth over breadth.
- **Drop for now:** Boyd optimization and standalone probability theory — pull in only if a specific analysis demands them.

**Meta-point:** a notes-and-reading approach signals *preparation*; a benchmark repo + report + a reached-out author signals *research capability*. For the PhD transition, the second is worth far more.
