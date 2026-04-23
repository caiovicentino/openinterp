# OpenInterp

> Watch language models think. Open source interpretability for everyone.

**Live**: [openinterp.org](https://openinterp.org) (coming soon) · [HuggingFace Space](https://huggingface.co/spaces/caiovicentino1/openinterp)

---

## What this is

OpenInterp is an open source interpretability platform with four pillars:

| Pillar | What | Status |
|---|---|---|
| 🔬 **Observatory** | Trace Theater, Circuit Canvas, Atlas search, N-way Comparison | **Q1 2026 · MVP live** |
| 🧪 **Laboratory** | Sandbox, Recipe Store, Auto-Interp, Counterfactual Studio | Q2 2026 |
| 🛡️ **Watchtower** | Feature Firehose API, Safety Watchlist, Audit Trail — Enterprise SaaS | Q4 2026 |
| 🎓 **Academy** | Expeditions, Interp Olympics, Live Lectures, Reproducibility Vault | Q3 2026 |

**Positioning**: Neuronpedia is the encyclopedia you consult. OpenInterp is the microscope, the lab, the watchtower, and the school — a tab you leave open.

---

## What's shipped today (v0)

- **This landing + manifesto** (`index.html`): single-file HTML, zero-login, mobile-first.
- **Trace Theater v0**: scripted demo on Qwen3.6-27B with real feature IDs from our SAE work:
  - `f2503` overconfidence pattern
  - `f3383` medical domain terms
  - `f1847` urgency assessment
  - ...10 features total, per-token heatmap, intervention slider with counterfactuals.
- **Grounded in published research**:
  - [`qwen36-27b-sae-multilayer`](https://huggingface.co/caiovicentino1/qwen36-27b-sae-multilayer) — 3 TopK SAEs on L11/L31/L55
  - [`qwen36-27b-sae-papergrade`](https://huggingface.co/caiovicentino1/qwen36-27b-sae-papergrade) — n=65k paper-grade SAEs (training in progress)
  - [`qwen36-deepconf-probe`](https://huggingface.co/caiovicentino1/qwen36-deepconf-probe) — +6pp SuperGPQA via probe-weighted voting
  - [`qwen36-feature-circuits`](https://huggingface.co/caiovicentino1/qwen36-feature-circuits) — honest negative result

---

## Running locally

```bash
git clone https://github.com/caiovicentino/openinterp
cd openinterp
python3 -m http.server 8080
# open http://localhost:8080
```

Zero dependencies. Static HTML. Works offline.

---

## Deploying

### HuggingFace Space (recommended)

```bash
huggingface-cli upload caiovicentino1/openinterp index.html --repo-type=space
```

### GitHub Pages

```bash
gh repo create caiovicentino/openinterp --public --source=. --push
# then enable Pages in repo settings → main branch
```

### Custom domain

Point `openinterp.org` A/CNAME to HF Space or GitHub Pages.

---

## What we uniquely bring

- **First public SAE on the Qwen3.6 family** — dense (27B) + MoE (35B-A3B). Verified against HuggingFace search at shipping time.
- **Hybrid architecture expertise** — first SAEs on Gated Delta Networks (Qwen3.5, Qwen3.6 hybrid MoE).
- **Probe-based uncertainty** — L11 LogReg probe ships as a calibration overlay for any trace.
- **Saturation detector** — identifies where the model stopped thinking usefully.
- **Honest negatives** — we publish the feature-circuits result that failed replication. Trust comes from admitting failure.

---

## The three moats

1. **Cross-model Rosetta Stone** — a graph of feature equivalences across Qwen, Gemma, Llama, Claude, Mistral. Years to replicate.
2. **Watchtower revenue flywheel** — B2B API pays for the OSS tier. Free where it matters, profitable where it sustains.
3. **Model Partner Program** — agreements with model vendors to ship SAEs at release. "X launched with OpenInterp" becomes standard.

---

## Roadmap

| Quarter | Theme | Ships |
|---|---|---|
| Q1 2026 · **NOW** | Observatory v0 | Trace Theater · paper-grade SAEs · this landing · API v0.1 |
| Q2 2026 | Expansion | Atlas search · Circuit Canvas · Lab beta · academic paper |
| Q3 2026 | Community | Recipe Store · Expeditions · Olympics Season 1 · 1k MAU |
| Q4 2026 | Sustainability | Watchtower Enterprise beta · Model Partner Program · Repro Vault |

---

## Contributing

All code is MIT. All SAEs are public on HuggingFace. All research steps — including the failures — are documented.

Ways in:
- **File a feature request** — issues tab, tag `[feature]`
- **Publish a SAE** — open a PR adding your model to the Atlas registry
- **Write an Expedition** — propose a tutorial in `academy/` (Q3)
- **Watchtower design partner** — email satoshimemes79@gmail.com

---

## Credits

Standing on the shoulders of:

- [**Neuronpedia**](https://neuronpedia.org) — the first SAE encyclopedia; baseline of the ecosystem.
- [**Gemma Scope**](https://huggingface.co/google/gemma-scope) — reference SAE suite (Lieberum et al. 2024).
- [**Gao et al. 2024**](https://arxiv.org/abs/2406.04093) — TopK SAE + AuxK recipe we use for paper-grade training.
- [**Anthropic Transformer Circuits thread**](https://transformer-circuits.pub) — the spiritual predecessor.
- [**SAELens**](https://github.com/jbloomAus/SAELens) — our checkpoint format.
- [**DFlash / Luce-Org**](https://github.com/Luce-Org/lucebox-hub) — shared interest in consumer-GPU interpretability.

Built by [Caio Vicentino](https://huggingface.co/caiovicentino1) · MIT License · 2026
