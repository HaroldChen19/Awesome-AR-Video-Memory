<h1 align="center">
  <strong>The Past Frames the Future:</strong>
  
  <strong>Memory for Autoregressive Video Generation --- A Survey</strong>
</h1>

<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-Awesome--AR--Video--Memory-181717?logo=github)](https://github.com/RongjinGuo/Awesome-AR-Video-Memory)
[![Website](https://img.shields.io/badge/Website-AR_Video_Memory-a9432d)](https://rongjinguo.github.io/Awesome-AR-Video-Memory/)
[![GitHub stars](https://img.shields.io/github/stars/HaroldChen19/Awesome-AR-Video-Memory?style=social)](https://github.com/HaroldChen19/Awesome-AR-Video-Memory/stargazers)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

## 📢 News

- [2026/09] The repository launches with the methods and benchmarks from the survey taxonomy tables.

## 📜 Overview

[Introduction](#introduction) | [Taxonomy](#memory-carrier-taxonomy) | [Paper List](#paper-list) | [Benchmarks](#benchmarks) | [Citation](#citation) | [Contact](#contact)




## 👋 Introduction

<div align="center">
  <img src="assets/figure_1.png" alt="Overview of memory mechanisms in autoregressive video generation." width="85%" />
  <p><em>Overview of memory mechanisms in autoregressive video generation. Memory mechanisms preserve historical information beyond the active context to support long-horizon generation.</em></p>

</div>

This repository accompanies **_The Past Frames the Future: Memory for Autoregressive Video Generation — A Survey_** and provides a curated collection of memory mechanisms for autoregressive (AR) video generation and world modeling.

AR video models generate visual sequences through causal, step-wise rollouts. However, while historical dependencies continuously grow, practical systems operate with bounded context windows, storage, and computation. Memory mechanisms address this gap by preserving and reusing historical information after it leaves the active context, enabling long-term consistency of entities, scenes, dynamics, semantics, and causal changes.

Following our survey, this repository organizes existing methods from five complementary perspectives:

- **Forms**: what carries historical information;
- **Functions**: what information memory preserves;
- **Operations**: how memory is written, read, updated, managed, and integrated;
- **Learning**: how memory behaviors are acquired;
- **Evaluation**: how memory capabilities are measured.

The paper list in this repository is primarily organized by **Forms**, i.e., the underlying memory carriers, which provide a unified view of diverse mechanisms across architectures and applications.



## 📦 Memory Carrier Taxonomy


<div align="center">
  <img src="assets/figure_forms.png" alt="Taxonomy of visual, implicit-state, explicit-state, and adaptive-parametric memory carriers for autoregressive video generation." width="80%" />
  <p><em>Memory carriers in autoregressive video generation. A system may combine multiple carrier families to condition future generation.</em></p>
</div>

We categorize memory mechanisms into four major carrier families:

- **Visual Memory:** Preserves observation-aligned frames, clips, or visual latents as reusable historical evidence.

- **Implicit State Memory:** Retains history in model-native latent states, such as attention caches or recurrent states, without predefined semantic or geometric structures.

- **Explicit State Memory:** Represents history through structured and interpretable states, including entities, geometry, scenes, events, and relations.

- **Adaptive Parametric Memory:** Stores sequence- or experience-specific information through adapted parameters, modular weights, or parameter updates.


## 📂 Paper List

**Paper List:** [Visual](#visual-memory) | [Implicit State](#implicit-state-memory) | [Explicit State](#explicit-state-memory) | [Adaptive Parametric](#adaptive-parametric-memory)

<!-- METHODS:START -->
### Visual Memory

#### Pixel-space Visual Memory

- [2026/06] Retrieve What's Missing: Coverage-Maximizing Retrieval for Consistent Long Video Generation. [[paper](https://arxiv.org/abs/2606.02479)]
- [2026/03] I3DM: Implicit 3D-aware Memory Retrieval and Injection for Consistent Video Scene Generation. [[paper](https://arxiv.org/abs/2603.23413)]
- [2026/02] Pathwise test-time correction for autoregressive long video generation. [[paper](https://arxiv.org/abs/2602.05871)]
- [2026/01] Plenoptic video generation. [[paper](https://arxiv.org/abs/2601.05239)]
- [2025/12] Worldpack: Compressed memory improves spatial consistency in video world modeling. [[paper](https://arxiv.org/abs/2512.02473)]
- [2025/04] WorldMem: Long-term Consistent World Simulation with Memory. [[paper](https://arxiv.org/abs/2504.12369)]
- [2025/01] Context as memory: Scene-consistent interactive long video generation with memory retrieval. [[paper](https://scholar.google.com/scholar?q=Context+as+memory%3A+Scene-consistent+interactive+long+video+generation+with+memory+retrieval)]
- [2025/01] Vmem: Consistent interactive video scene generation with surfel-indexed view memory. [[paper](https://scholar.google.com/scholar?q=Vmem%3A+Consistent+interactive+video+scene+generation+with+surfel-indexed+view+memory)]
- [2024/01] Art• v: Auto-regressive text-to-video generation with diffusion models. [[paper](https://scholar.google.com/scholar?q=Art%E2%80%A2+v%3A+Auto-regressive+text-to-video+generation+with+diffusion+models)]

#### VAE-space Visual Memory

- [2026/06] LongLive-RAG: A General Retrieval-Augmented Framework for Long Video Generation. [[paper](https://arxiv.org/abs/2606.02553)]
- [2026/06] MemLearner: Learning to Query Context memory for Video World Models. [[paper](https://arxiv.org/abs/2606.31734)]
- [2026/04] Matrix-game 3.0: Real-time and streaming interactive world model with long-horizon memory. [[paper](https://arxiv.org/abs/2604.08995)]
- [2026/03] MemCam: Memory-Augmented Camera Control for Consistent Video Generation. [[paper](https://arxiv.org/abs/2603.26193)]
- [2026/03] MosaicMem: Hybrid Spatial Memory for Controllable Video World Models. [[paper](https://arxiv.org/abs/2603.17117)]
- [2026/03] Out of sight but not out of mind: Hybrid memory for dynamic video world models. [[paper](https://arxiv.org/abs/2603.25716)]
- [2026/02] UCM: Unified Modeling of Camera Control and Memory with Time-aware Positional Encoding Warping for World Models. [[paper](https://arxiv.org/abs/2602.22960)]
- [2026/01] Frame context packing and drift prevention in next-frame-prediction video diffusion models. [[paper](https://scholar.google.com/scholar?q=Frame+context+packing+and+drift+prevention+in+next-frame-prediction+video+diffusion+models)]
- [2025/12] WorldPlay: Towards Long-Term Geometric Consistency for Real-Time Interactive World Modeling. [[paper](https://arxiv.org/abs/2512.14614)]
- [2025/11] MagicWorld: Towards Long-Horizon Stability for Interactive Video World Exploration. [[paper](https://arxiv.org/abs/2511.18886)]
- [2025/01] Streamingt2v: Consistent, dynamic, and extendable long video generation from text. [[paper](https://scholar.google.com/scholar?q=Streamingt2v%3A+Consistent%2C+dynamic%2C+and+extendable+long+video+generation+from+text)]

### Implicit State Memory

#### Attention-cache States

- [2026/07] Closing the Loop: Training-Free Revisit Consistency for Autoregressive Generative Rendering. [[paper](https://arxiv.org/abs/2607.21848)]
- [2026/06] FadeMem: Distance-Aware Memory Consolidation for Autoregressive Video Diffusion. [[paper](https://arxiv.org/abs/2606.10671)]
- [2026/05] Attend Locally, Remember Linearly: Linear Attention as Cross-Frame Memory for Autoregressive Video Diffusion. [[paper](https://arxiv.org/abs/2605.16579)]
- [2026/05] Future Forcing: Future-aware Training-free KV Cache Policy for Autoregressive Video Generation. [[paper](https://arxiv.org/abs/2605.30083)]
- [2026/05] OmniMem: Scalable and Adaptive Memory Retrieval for Long Video Generation. [[paper](https://arxiv.org/abs/2605.30519)]
- [2026/05] SlotMemory: Object-Centric KV Memory for Streaming Long-Video Generation. [[paper](https://arxiv.org/abs/2605.31033)]
- [2026/04] Grounded forcing: Bridging time-independent semantics and proximal dynamics in autoregressive video synthesis. [[paper](https://arxiv.org/abs/2604.06939)]
- [2026/04] Long-Horizon Streaming Video Generation via Hybrid Attention with Decoupled Distillation. [[paper](https://arxiv.org/abs/2604.10103)]
- [2026/04] Sparse forcing: Native trainable sparse attention for real-time autoregressive diffusion video generation. [[paper](https://arxiv.org/abs/2604.21221)]
- [2026/03] Anchor Forcing: Anchor Memory and Tri-Region RoPE for Interactive Streaming Video Diffusion. [[paper](https://arxiv.org/abs/2603.13405)]
- [2026/03] Memrope: Training-free infinite video generation via evolving memory tokens. [[paper](https://arxiv.org/abs/2603.12513)]
- [2026/03] PackForcing: Short Video Training Suffices for Long Video Sampling and Long Context Inference. [[paper](https://arxiv.org/abs/2603.25730)]
- [2026/03] Relax forcing: Relaxed kv-memory for consistent long video generation. [[paper](https://arxiv.org/abs/2603.21366)]
- [2026/02] Context forcing: Consistent autoregressive video generation with long context. [[paper](https://arxiv.org/abs/2602.06028)]
- [2026/01] Rolling forcing: Autoregressive long video diffusion in real time. [[paper](https://scholar.google.com/scholar?q=Rolling+forcing%3A+Autoregressive+long+video+diffusion+in+real+time)]
- [2025/12] Egolcd: Egocentric video generation with long context diffusion. [[paper](https://arxiv.org/abs/2512.04515)]
- [2025/12] Memorize-and-generate: Towards long-term consistency in real-time video generation. [[paper](https://arxiv.org/abs/2512.18741)]
- [2025/12] Relic: Interactive video world model with long-horizon memory. [[paper](https://arxiv.org/abs/2512.04040)]
- [2025/11] BIFE: Better Interaction, Fewer Errors for Minute-Long Video Generation. [[paper](https://arxiv.org/abs/2511.22973)]
- [2025/09] Longlive: Real-time interactive long video generation. [[paper](https://arxiv.org/abs/2509.22622)]

#### Recurrent and State-space States

- [2026/07] Surprise Forcing: What to Remember, When to Skip in Long Video Generation. [[paper](https://arxiv.org/abs/2607.18436)]
- [2026/06] Compression and Retrieval: Implicit Memory Retrieval for Video World Models. [[paper](https://arxiv.org/abs/2606.23105)]
- [2026/06] Echo-Infinity: Learning Evolving Memory for Real-Time Infinite Video Generation. [[paper](https://arxiv.org/abs/2606.04527)]
- [2026/02] Infinite-world: Scaling interactive world models to 1000-frame horizons via pose-free hierarchical memory. [[paper](https://arxiv.org/abs/2602.02393)]
- [2025/12] Videossm: Autoregressive long video generation with hybrid state-space memory. [[paper](https://arxiv.org/abs/2512.04519)]
- [2025/10] Pack and Force Your Memory: Long-form and Consistent Video Generation. [[paper](https://arxiv.org/abs/2510.01784)]
- [2025/05] StateSpaceDiffuser: Bringing Long Context to Diffusion World Models. [[paper](https://arxiv.org/abs/2505.22246)]
- [2025/02] Malt diffusion: Memory-augmented latent transformers for any-length video generation. [[paper](https://arxiv.org/abs/2502.12632)]
- [2025/01] Long-context state-space video world models. [[paper](https://scholar.google.com/scholar?q=Long-context+state-space+video+world+models)]

#### Encoded History States

- [2026/06] Geometry-Aware Implicit Memory for Video World Models. [[paper](https://arxiv.org/abs/2606.02436)]
- [2025/12] TinyHistory: Lightweight Video History Embeddings via Two-Stage Context Learning. [[paper](https://arxiv.org/abs/2512.23851)]

### Explicit State Memory

#### Entity-centric States

- [2026/06] Closed-Loop Triplet Synergistic Generation for Long-Form Video. [[paper](https://arxiv.org/abs/2606.16184)]
- [2026/05] A ^2 RD: Agentic Autoregressive Diffusion for Long Video Consistency. [[paper](https://arxiv.org/abs/2605.06924)]
- [2026/05] ReCA: Multi-Shot Long Video Extrapolation via Recursive Context Allocation. [[paper](https://arxiv.org/abs/2605.26525)]
- [2026/04] ActionParty: Multi-Subject Action Binding in Generative Video Games. [[paper](https://arxiv.org/abs/2604.02330)]
- [2026/01] Videomemory: Toward consistent video generation via memory integration. [[paper](https://arxiv.org/abs/2601.03655)]

#### Spatial and Geometric States

- [2026/06] Latent spatial memory for video world models. [[paper](https://arxiv.org/abs/2606.09828)]
- [2026/03] Liveworld: Simulating out-of-sight dynamics in generative video world models. [[paper](https://arxiv.org/abs/2603.07145)]
- [2026/03] WorldStereo: Bridging Camera-Guided Video Generation and Scene Reconstruction via 3D Geometric Memories. [[paper](https://arxiv.org/abs/2603.02049)]
- [2026/02] Anchorweave: World-consistent video generation with retrieved local spatial memories. [[paper](https://arxiv.org/abs/2602.14941)]
- [2026/01] Beyond pixel histories: World models with persistent 3d state. [[paper](https://scholar.google.com/scholar?q=Beyond+pixel+histories%3A+World+models+with+persistent+3d+state)]
- [2026/01] Learning 3d persistent embodied world models. [[paper](https://scholar.google.com/scholar?q=Learning+3d+persistent+embodied+world+models)]
- [2026/01] Spatia: Video generation with updatable spatial memory. [[paper](https://scholar.google.com/scholar?q=Spatia%3A+Video+generation+with+updatable+spatial+memory)]
- [2026/01] Video world models with long-term spatial memory. [[paper](https://scholar.google.com/scholar?q=Video+world+models+with+long-term+spatial+memory)]
- [2025/10] EvoWorld: Evolving Panoramic World Generation with Explicit 3D Memory. [[paper](https://arxiv.org/abs/2510.01183)]
- [2025/10] Memory forcing: Spatio-temporal memory for consistent scene generation on minecraft. [[paper](https://arxiv.org/abs/2510.03198)]
- [2025/06] Deepverse: 4d autoregressive video generation as a world model. [[paper](https://arxiv.org/abs/2506.01103)]
- [2025/01] Voyager: Long-range and world-consistent video diffusion for explorable 3d scene generation. [[paper](https://scholar.google.com/scholar?q=Voyager%3A+Long-range+and+world-consistent+video+diffusion+for+explorable+3d+scene+generation)]

### Adaptive Parametric Memory

#### Internal Parametric Memory

- [2026/07] Towards Memory-Efficient Autoregressive Video Generation via Instance-Specific Parametric Absorption. [[paper](https://arxiv.org/abs/2607.00712)]
- [2026/01] HippoCampus: Hierarchical Memory for Long-Horizon Video World Models. [[paper](https://scholar.google.com/scholar?q=HippoCampus%3A+Hierarchical+Memory+for+Long-Horizon+Video+World+Models)]
- [2026/01] Test-time training done right. [[paper](https://scholar.google.com/scholar?q=Test-time+training+done+right)]
- [2025/11] Recurrent Autoregressive Diffusion: Global Memory Meets Local Attention. [[paper](https://arxiv.org/abs/2511.12940)]
- [2025/01] Slowfast-vgen: Slow-fast learning for action-driven long video generation. [[paper](https://scholar.google.com/scholar?q=Slowfast-vgen%3A+Slow-fast+learning+for+action-driven+long+video+generation)]

#### Modular Parametric Memory

- _No records yet._
<!-- METHODS:END -->

## 🗃️ Benchmarks

Benchmarks are organized by their evidence role. `MD` means **memory dependence**: `required` requires prior rollout history, `subset` applies only to a designated protocol or track, and `not-required` measures a related sequence-level behavior without making history necessary for the query.

<!-- BENCHMARKS:START -->
### Memory-oriented Benchmarks

- [2026/06] Current World Models Lack a Persistent State Core. [Targets: entity, spatial, state, action] [MD: subset]. Hidden-and-returned state. [[paper](https://arxiv.org/abs/2606.20545)] [[code](https://github.com/JinPLu/WRBench)]
- [2026/06] Mbench: A comprehensive benchmark on memory capability for video world models. [Targets: entity, spatial, state, action] [MD: subset]. Triggered memory tests. [[paper](https://arxiv.org/abs/2606.00793)] [[code](https://github.com/study-overflow/MBench)]
- [2026/06] MemoBench: Benchmarking World Modeling in Dynamically Changing Environments. [Targets: entity, spatial, state] [MD: required]. Disappear-reappear. [[paper](https://arxiv.org/abs/2606.27537)] [[code](https://github.com/MemoBench-Team/MemoBench)]
- [2026/06] WorldRoamBench: An Open-World Benchmark for Long-Horizon Stability of Interactive World Models. [Targets: entity, spatial, action] [MD: subset]. Executed-path revisit. [[paper](https://arxiv.org/abs/2606.31672)] [[project](https://worldroam.amap.com/)]
- [2026/05] EntityBench: Towards Entity-Consistent Long-Range Multi-Shot Video Generation. [Targets: entity] [MD: required]. Name-only reappearance. [[paper](https://arxiv.org/abs/2605.15199)] [[code](https://github.com/Catherine-R-He/EntityBench)]
- [2026/05] iWorld-Bench: A Benchmark for Interactive World Models with a Unified Action Generation Framework. [Targets: spatial, action] [MD: subset]. Reciprocal camera return. [[paper](https://arxiv.org/abs/2605.03941)] [[code](https://github.com/EmbodiedCity/iWorld-Bench)]
- [2026/05] Wbench: A comprehensive multi-turn benchmark for interactive video world model evaluation. [Targets: entity, spatial, state, action] [MD: subset]. Gated round-trip return. [[paper](https://arxiv.org/abs/2605.25874)] [[code](https://github.com/meituan-longcat/WBench)]
- [2026/03] Liveworld: Simulating out-of-sight dynamics in generative video world models. [Targets: entity, spatial, state, action] [MD: required]. Same-/different-pose revisit. [[paper](https://arxiv.org/abs/2603.07145)] [[code](https://github.com/ZichengDuan/LiveWorld)]
- [2026/03] Out of sight, out of mind? evaluating state evolution in video world models. [Targets: state, action] [MD: required]. Hidden process evolution. [[paper](https://arxiv.org/abs/2603.13215)] [[code](https://github.com/jhanliufu-personal/STEVO-Bench)]
- [2026/02] Mind: Benchmarking memory consistency and action control in world models. [Targets: spatial, action] [MD: subset]. Revisit / symmetric paths. [[paper](https://arxiv.org/abs/2602.08025)] [[code](https://github.com/CSU-JPG/MIND)]
- [2026/02] UCM: Unified Modeling of Camera Control and Memory with Time-aware Positional Encoding Warping for World Models. [Targets: spatial, action] [MD: subset]. Reverse-cycle / memory init.. [[paper](https://arxiv.org/abs/2602.22960)] [[code](https://github.com/HumanAIGC/UCM)]
- [2025/12] Memorize-and-generate: Towards long-term consistency in real-time video generation. [Targets: spatial] [MD: required]. Symmetric leave-return. [[paper](https://arxiv.org/abs/2512.18741)] [[code](https://github.com/Xilluill/MAG)]
- [2025/05] LoopNav: Benchmarking Spatial Consistency in World Models. [Targets: spatial] [MD: required]. Loop-based spatial consistency. [[paper](https://arxiv.org/abs/2505.22976)] [[code](https://github.com/Kevin-lkw/LoopNav)]

### Sequence Stress Tests

- [2026/06] Groundshot: Visually consistent multi-shot long video generation via entity-grounded shot scheduling. [Targets: entity, state] [MD: not-required]. Reference-grounded recurrence. [[paper](https://arxiv.org/abs/2606.20799)]
- [2026/06] UnityShots: Memory-Driven Multi-Shot Audio-Video Generation with Boundary-Aware Gating. [Targets: entity] [MD: subset]. Audio-visual shot continuity. [[paper](https://arxiv.org/abs/2606.21661)] [[code](https://github.com/JIA-Lab-research/UnityShots)]
- [2026/06] WorldOlympiad: Can Your World Model Survive a Triathlon?. [Targets: spatial, state, action] [MD: not-required]. Stitched world rollouts. [[paper](https://arxiv.org/abs/2606.11129)] [[code](https://github.com/alibaba-damo-academy/WorldOlympiad)]
- [2026/05] Advancing Narrative Long Video Generation via Training-Free Identity-Aware Memory. [Targets: entity, state, action] [MD: subset]. Prompt-stream continuity. [[paper](https://arxiv.org/abs/2605.18733)] [[code](https://github.com/Eddie0521/IAMFlow)]
- [2026/05] DirectorBench: Diagnosing Long-Form Video Generation with Personalized Multi-Agent Evaluation. [Targets: entity, spatial, state] [MD: not-required]. Workflow checkpoints. [[paper](https://arxiv.org/abs/2605.30090)] [[code](https://github.com/jiaminchen-1031/DirectorBench)]
- [2026/05] LongAV-Compass: Towards Unified Evaluation of Minute-Scale Audio-Visual Generation Across T2AV, I2AV, and V2AV. [Targets: entity, state] [MD: not-required]. Multimodal continuity. [[paper](https://arxiv.org/abs/2605.26244)] [[code](https://github.com/pkucs-Ltf/LongAV-Compass)]
- [2026/05] ReCA: Multi-Shot Long Video Extrapolation via Recursive Context Allocation. [Targets: entity, spatial, state] [MD: not-required]. Source-grounded extrapolation. [[paper](https://arxiv.org/abs/2605.26525)] [[project](https://reca.vmv.re/)]
- [2026/04] Long-CODE: Isolating Pure Long-Context as an Orthogonal Dimension in Video Evaluation. [Targets: entity, state] [MD: not-required]. Structural corruption. [[paper](https://arxiv.org/abs/2604.17428)] [[code](https://github.com/ZhijiangTang/Long-CODE)]
- [2026/04] WorldMark: A Unified Benchmark Suite for Interactive Video World Models. [Targets: spatial, action] [MD: subset]. Action and revisit tests. [[paper](https://arxiv.org/abs/2604.21686)] [[code](https://github.com/AlayaLab/WorldMark)]
- [2026/01] Msvbench: Towards human-level evaluation of multi-shot video generation. [Targets: entity, spatial, state] [MD: not-required]. Hierarchical multi-shot eval.. [[paper](https://scholar.google.com/scholar?q=Msvbench%3A+Towards+human-level+evaluation+of+multi-shot+video+generation)] [[code](https://github.com/HITsz-TMG/MSVBench)]
- [2026/01] Narrlv: Towards a comprehensive narrative-centric evaluation for long video generation. [Targets: entity, state] [MD: not-required]. Narrative-atom evaluation. [[paper](https://scholar.google.com/scholar?q=Narrlv%3A+Towards+a+comprehensive+narrative-centric+evaluation+for+long+video+generation)] [[code](https://github.com/AMAP-ML/NarrLV)]
- [2025/11] BIFE: Better Interaction, Fewer Errors for Minute-Long Video Generation. [Targets: entity, spatial, state] [MD: not-required]. Block-wise drift (VDE). [[paper](https://arxiv.org/abs/2511.22973)] [[code](https://github.com/alibaba-damo-academy/BIFE)]
- [2025/10] LoCoT2V-Bench: Benchmarking Long-Form and Complex Text-to-Video Generation. [Targets: entity, spatial, state] [MD: not-required]. Local/global consistency. [[paper](https://arxiv.org/abs/2510.26412)] [[code](https://github.com/XqZeppelinhead0702/LoCoT2V-Bench)]
- [2025/01] Is your world simulator a good story presenter? a consecutive events-based benchmark for future long video generation. [Targets: entity, state] [MD: not-required]. Ordered event realization. [[paper](https://scholar.google.com/scholar?q=Is+your+world+simulator+a+good+story+presenter%3F+a+consecutive+events-based+benchmark+for+future+long+video+generation)] [[code](https://github.com/ypwang61/StoryEval)]
- [2025/01] SeqBench: Benchmarking Sequential Narrative Generation in Text-to-Video Models. [Targets: entity, state] [MD: not-required]. Sequential narratives. [[paper](https://scholar.google.com/scholar?q=SeqBench%3A+Benchmarking+Sequential+Narrative+Generation+in+Text-to-Video+Models)] [[code](https://github.com/TangZhengxu/SeqBench-Benchmarking-Sequential-Narrative-Generation-in-Text-to-Video-Models)]
- [2025/01] Vbench++: Comprehensive and versatile benchmark suite for video generative models. [Targets: entity, spatial, state] [MD: not-required]. Long-range visible consistency. [[paper](https://scholar.google.com/scholar?q=Vbench%2B%2B%3A+Comprehensive+and+versatile+benchmark+suite+for+video+generative+models)] [[code](https://github.com/Vchitect/VBench/tree/master/vbench2_beta_long)]
- [2024/01] Chronomagic-bench: A benchmark for metamorphic evaluation of text-to-time-lapse video generation. [Targets: state] [MD: not-required]. Visible process progression. [[paper](https://scholar.google.com/scholar?q=Chronomagic-bench%3A+A+benchmark+for+metamorphic+evaluation+of+text-to-time-lapse+video+generation)] [[code](https://github.com/PKU-YuanGroup/ChronoMagic-Bench)]
- [2023/01] Storybench: A multifaceted benchmark for continuous story visualization. [Targets: entity, spatial, state] [MD: not-required]. Story-level consistency. [[paper](https://scholar.google.com/scholar?q=Storybench%3A+A+multifaceted+benchmark+for+continuous+story+visualization)] [[code](https://github.com/google/storybench)]
- [2023/01] Temporally consistent transformers for video generation. [Targets: spatial, state] [MD: subset]. Horizon-wise fidelity. [[paper](https://scholar.google.com/scholar?q=Temporally+consistent+transformers+for+video+generation)] [[code](https://github.com/wilson1yan/teco)]
<!-- BENCHMARKS:END -->

## 🏷️ Citation

If this repository is helpflu for your research, a citation would be greatly appreciated:

```bibtex
@article{chen2026past,
  title = {The Past Frames the Future: Memory for Autoregressive Video Generation},
  author = {Harold Haodong Chen and Rongjin Guo and Disen Lan and Wen-Jie Shu and Hongfei Zhang and others},
  year = {2026},
  note = {TBD}
}
```

## 📬 Contact

For questions about the survey or the paper list, feel free to open a GitHub issue or contact [Rongjin Guo](mailto:guorong3529@gmail.com) / [Harold Chen](mailto:haroldchen19@gmail.com).

## 🌟 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=HaroldChen19/Awesome-AR-Video-Memory&type=date&legend=top-left)](https://www.star-history.com/#HaroldChen19/Awesome-AR-Video-Memory&type=date&legend=top-left)

## 🔰 License

The repository is released under the [MIT License](LICENSE).
