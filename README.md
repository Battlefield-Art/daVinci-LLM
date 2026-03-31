# daVinci-LLM: Towards the Science of Pretraining

<div align="center">

[![Paper](https://img.shields.io/badge/📄_Paper-arXiv-red)](https://arxiv.org/abs/2603.27164)
[![Dataset](https://img.shields.io/badge/🤗_Dataset-davinci--llm--data-yellow)](https://huggingface.co/datasets/SII-GAIR-NLP/davinci-llm-data)
[![Model](https://img.shields.io/badge/🤗_Model-davinci--llm--model-blue)](https://huggingface.co/SII-GAIR-NLP/davinci-llm-model)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

</div>


$$
\huge\textbf{Democratic Pretraining: Probably The Most Transparent and Reproducible Model}
$$

## 🔬 Why This Project Matters

> [!IMPORTANT]
> **Open-source ≠ Transparent.** While we can download weights, the scientific process remains hidden. **daVinci-LLM** fixes this by releasing the full recipe: 200+ ablations, data pipelines, and training logic.

<div align="center">
  <img src="fig/score-daVinci-llm.png" alt="daVinci-LLM overview" width="100%" />
</div>

While open-weight models release only checkpoints, critical pretraining details—data compositions, mixture ratios, training dynamics—remain undisclosed. **daVinci-LLM**, developed by the **GAIR-NLP group at Shanghai Innovation Institute (SII)**, addresses this gap with a fully-open paradigm—releasing not only weights, but **200+ controlled ablation results**, complete data pipelines, training decision logic, and even failed attempts, so the community can understand *why* the model was trained this way, not merely *what* it produced.

daVinci-LLM is not merely a pretrained model release, but an infrastructure for **Democratizing Pretraining Research**. Our goal is to transform pretraining from "black magic requiring industrial-scale resources" into "**scientific exploration that any team can participate in**".

## 🎁 Open-Source Artifacts

We publicly release the following artifacts to facilitate reproducibility and support the research community:

| Category | Content |
|----------|---------|
| 🤗 **Model Weights** | Final model and **ALL** intermediate checkpoints (saved every 5,000 steps) |
| 📁 **Datasets** | 7.5T+ fully traceable Data Darwinism processed high quality pretrain dataset |
| 📊 **Data Processing Method** | Complete prompts for generative refinement and cognitive completion; filtering, deduplication, and synthesis code |
| ✅ **Evaluation Suite** | All 19 benchmark configurations and scoring code |
| 📄 **Technical Report** | Complete decision-making logic with 200+ ablation results |
| 🔧 **Pretrain Toolkit** (Comming soon)| A practical toolkit that packages daVinci’s pretraining know-how into reusable components for dataset refinement, recipe tuning, checkpoint reuse, and training health analysis—making pretraining more accessible reproducible, and efficient for researchers.

## 🆚 Differentiation from Existing Work

| Dimension | LLaMA/Qwen | OLMo | daVinci |
|---|---|---|---|
| Core Contribution | Model weights | Training framework (OLMo Core) | Scientific methodology + data assets |
| Degree of Openness | Only model weights are released | Engineering implementation is transparent | Complete decision process + 200+ experiments |
| Cost of Reuse | Training cannot be reproduced | Requires learning a new framework | Compatible with mainstream tools, with **zero migration cost** |
| Target Users | Users focused only on inference or fine-tuning | Teams with full training resources | **Resource-constrained teams that still want to conduct pretraining research** |

daVinci provides a **methodology for using any tool well**. Rather than reinventing the wheel, we show the community how to use existing frameworks such as Megatron in a more scientific and effective way. This methodological contribution is more durable than any single training framework: frameworks may become outdated as hardware evolves, but scientific methodology can remain valuable for the next decade.

## 🏛️ Three Pillars of Full Openness

daVinci-LLM is structured around three pillars, each contributing to transparency and reproducibility:

### 1. 📊 Data Transparency — The Data Darwinism Framework

We adopt the **Data Darwinism framework** to systematically organize data processing from L0 (raw acquisition) to L9 (full synthesis). Our **7.5T+ token** corpus combines publicly available datasets with our own processed and **openly released** data—every source is annotated with its Darwin Level, making processing decisions transparent and enabling researchers to assess quality depth and reuse our data assets.

<div align="center">
  <img src="fig/data-level.png" alt="Data Darwinism levels" width="90%" />
</div>

| Level | Operation | What It Does |
|-------|-----------|--------------|
| **L0** | Data Acquisition | Collect raw data from diverse sources |
| **L1** | Format Normalization | Convert heterogeneous formats into unified text |
| **L2** | Rule-Based Filtering | Remove duplicates, malformed text, non-target languages |
| **L3** | Model-Based Filtering | Assess educational value and domain relevance via classifiers |
| **L4** | Generative Refinement | Remove structural noise and repair content while preserving semantics |
| **L5** | Cognitive Completion | Make implicit reasoning explicit (e.g., expand compressed logical steps) |
| **L6–L9** | Higher-Order Synthesis | Contextual/environment/ecosystem synthesis (theoretical frontier) |

> 📖 **For the complete Data Darwinism framework**: See [Data Darwinism](https://arxiv.org/abs/2602.07824)


### 2. 🎓 Training Transparency — Adaptive Two-Stage Curriculum

<div align="center">
  <img src="fig/train-traj.png" alt="Training & evaluation pipeline" width="95%" />
</div>

daVinci-LLM uses a **dynamically monitored, adaptively adjusted** two-stage curriculum:

- **Stage 1 (6T tokens)**: Builds broad foundations. Continuous evaluation reveals that general knowledge saturates early (~1T tokens) while code and science reasoning sustain growth beyond 4T—prompting progressive reallocation toward reasoning-intensive domains.

- **Stage 2 (2T tokens)**: Introduces structured QA data in a progressive curriculum. Stage 2-1 balances across domains to establish stability; Stage 2-2 intensifies QA concentration for targeted reasoning amplification—yielding a **+12.14 gain**.

### 3. 🧪 Scientific Transparency — 200+ Controlled Ablations

We transformed key pretraining decisions into systematically verifiable research questions. Through 200+ controlled experiments, we investigated:

<details>
<summary><b>📌 Does deeper data processing actually improve capabilities?</b></summary>

- L3 filtering: Modest gains on basic tasks (+3.4 on MBPP)
- L4 refinement: Substantial gains on complex reasoning (+7.0 on MATH)
- L5 synthesis: Strong domain alignment but limited transfer
- **Insight**: Processing depth is a complementary dimension to data volume scaling

</details>

<details>
<summary><b>📌 How should training adapt as capabilities mature differently?</b></summary>

- General knowledge plateaus at ~1T tokens; reasoning grows past 4T
- Domain rebalancing works initially, but hits limits
- Format shift (introducing QA) unlocks further growth
- **Insight**: No single mixture suffices—monitor and adapt

</details>

<details>
<summary><b>📌 Can we intensify reasoning without catastrophic forgetting?</b></summary>

- Extreme specialization triggers collapse
- Progressive strategy: balanced foundation (equal parts QA/code/science) → targeted intensification (70% QA)
- **Insight**: Balance first, then intensify

</details>

<details>
<summary><b>📌 Are our evaluation metrics reliable?</b></summary>

- PPL vs. generative evaluation can produce ranking reversals
- High-QA models show protocol-specific artifacts
- **Insight**: Report multiple protocols for complete capability profiles

</details>

> 💡 **Full ablation details, configurations, and negative results**: See [Section 4 of our technical report](https://arxiv.org/abs/2603.27164)


## 📊 Key Results: 3B Matches 7B


Our **daVinci-LLM-3B** achieves an overall score of **51.72**, matching OLMo-3 7B despite having less than half the parameters. Notably, it substantially outperforms on complex reasoning tasks like **MATH** (62.80 vs. OLMo-3’s 39.60), demonstrating the value of systematic, evidence-based pretraining.

| Capability Dimension | daVinci-3B | OLMo-3 7B | LLaMA-3.2-3B | Qwen-2.5-3B |
| -------------------- | ---------: | --------: | -----------: | ----------: |
| **Overall Perfomance**   |      **51.72** |     **51.65** |        37.58 |       51.44 |
| General Knowledge    |      52.96 |     55.13 |        51.08 |       55.16 |
| Code Generation      |      55.99 |     54.42 |        32.40 |       56.13 |
| Scientific Reasoning |      48.30 |     45.98 |        22.45 |       44.65 |
| MATH                 |      62.80 |     39.60 |         9.00 |       37.20 |


## 📚 Citation

If you find this work helpful, please consider citing:

```bibtex
@misc{qin2026davincillmtowardssciencepretraining,
      title={daVinci-LLM:Towards the Science of Pretraining},
      author={Yiwei Qin and Yixiu Liu and Tiantian Mi and Muhang Xie and Zhen Huang and Weiye Si and Pengrui Lu and Siyuan Feng and Xia Wu and Liming Liu and Ye Luo and Jinlong Hou and Qipeng Guo and Yu Qiao and Pengfei Liu},
      year={2026},
      eprint={2603.27164},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2603.27164},
}
```

If you use the Data Darwinism framework, please also cite:
```bibtex
@misc{qin2026datadarwinismiunlocking,
      title={Data Darwinism Part I: Unlocking the Value of Scientific Data for Pre-training}, 
      author={Yiwei Qin and Zhen Huang and Tiantian Mi and Weiye Si and Chenyang Zhou and Qipeng Guo and Siyuan Feng and Pengfei Liu},
      year={2026},
      eprint={2602.07824},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2602.07824}, 
}
```
