# 近期 AR Video Memory 论文逐篇核对 — 2026-10-10

## 范围与核对标准

- 时间窗：**2026-09-01 至 2026-10-10（按 arXiv 首次提交时间 UTC）**，覆盖约六周；截至检索时可见的最新候选提交于 10 月 8 日。修订时间单独记录。
- 仓库基线：[HaroldChen19/Awesome-AR-Video-Memory](https://github.com/HaroldChen19/Awesome-AR-Video-Memory/tree/e76757e60ad75c4ca891a1ea5604137a4afe025e)，commit `e76757e60ad75c4ca891a1ea5604137a4afe025e`。
- arXiv 三组分页查询得到 **967 条去重发现记录**，按主题筛出 100 篇，并补查多主体、3D、latent planning 与 VLA 邻接文献；本清单逐项筛查 **117 篇**。其中 **72 篇核对了相关正文段落**，其余为摘要筛查，验证级别写在 CSV/JSON 中。发现记录数量不等于全文核对数量。
- README 新增 **30 篇方法**、**1 篇记忆训练研究**、**1 篇 AR 记忆诊断研究**，以及 **4 个 Memory-oriented benchmark 条目**。去除方法/benchmark 的同论文重叠后，共 **34 篇新论文**。
- 主分类依据未来生成实际读取的持久载体；Functions、Operations、Learning、Evaluation 另记。几何检索地址不自动变成 Explicit State；离线训练的 compressor/adapter 不自动变成 Adaptive Parametric Memory。
- `method_sections` 表示已核对相关方法/协议段落，不表示复现代码、验证全部实验结论或比较所有历史版本。原文页码采用 **PDF 物理页码，从 1 开始**，并固定到所核对的 arXiv 版本。
- **严格 scope：autoregressive video generation model 的 memory。** 方法必须有 AR 帧/chunk/clip 生成依据，且生成器后续步骤实际读取跨步骤保留的历史；贡献须直接涉及该记忆的表示、写读、保留、压缩、重组或学习。chunk 内 diffusion 双向去噪允许，外部 agent 按顺序调用整段视频模型本身不足以证明 AR。
- Training/Evaluation 仅收录直接研究 AR generator memory 的工作。外部故事/游戏逻辑、独立几何渲染、VLA/latent planning、普通长视频训练或硬件 memory 节省不据此纳入。未确立 AR 路径者暂缓，不能推断为已证明无记忆。
- [逐篇 scope 复核](2026-10-10-scope-recheck.md) 为每个新增条目分别列 AR 依据和 memory 依据，并记录上一版收录撤回/角色修正；混合架构的评测只保留明确的 AR 子实验。

| 四类 Forms | 本次新增方法数 | 子类/补充说明 |
|---|---:|---|
| Visual Memory | 9 | Pixel 1；VAE 6；宿主相关的 Visual Memory Management 2 |
| Implicit State Memory | 19 | Attention-cache 16；Recurrent 2；Encoded History 1 |
| Explicit State Memory | 2 | Entity-centric 0；Spatial/Geometric 2 |
| Adaptive Parametric Memory | 0 | 已查 JEPA-TTT / Sandwich-Residuals，范围为 latent planning；暂不当作 AR 视频方法新增 |

## 可直接更新 README 的方法

| 首次提交 | 论文 | 主分类 | 副载体 | 正文依据 |
|---|---|---|---|---|
| 2026-10-08 | [WorldCast](https://arxiv.org/abs/2610.12412v1) | VAE-space Visual Memory | Explicit State | [PDF p.4](https://arxiv.org/pdf/2610.12412v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12412v1#page=5)；§3.2–3.3; player state and scene bank |
| 2026-10-08 | [Memory Forcing](https://arxiv.org/abs/2610.11756v1) | Attention-cache States | — | [PDF p.3](https://arxiv.org/pdf/2610.11756v1#page=3), [PDF p.5](https://arxiv.org/pdf/2610.11756v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.11756v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.11756v1#page=7)；§3.3; Algorithm 1; bank-aware RoPE |
| 2026-10-07 | [SGF+](https://arxiv.org/abs/2610.10429v2) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2610.10429v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.10429v2#page=5), [PDF p.6](https://arxiv.org/pdf/2610.10429v2#page=6)；§3.1–3.3; Eqs. (1), (2), (5) |
| 2026-10-06 | [SPW-Nav](https://arxiv.org/abs/2610.08941v1) | VAE-space Visual Memory | — | [PDF p.5](https://arxiv.org/pdf/2610.08941v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.08941v1#page=6)；§4.4; multi-scale memory compression |
| 2026-10-05 | [Keepsake](https://arxiv.org/abs/2610.06588v1) | Carrier-agnostic Visual Memory Management | — | [PDF p.4](https://arxiv.org/pdf/2610.06588v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.06588v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.06588v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.06588v1#page=7)；§3.1–3.3; Algorithm 1; §4.1 |
| 2026-10-05 | [HLA-WM](https://arxiv.org/abs/2610.05739v1) | Recurrent and State-space States | — | [PDF p.1](https://arxiv.org/pdf/2610.05739v1#page=1), [PDF p.5](https://arxiv.org/pdf/2610.05739v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.05739v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.05739v1#page=7)；§4.2–4.4; affine summaries and state recomposition |
| 2026-10-04 | [Artemis](https://arxiv.org/abs/2610.07031v1) | Spatial and Geometric States | Implicit State | [PDF p.5](https://arxiv.org/pdf/2610.07031v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.07031v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.07031v1#page=7)；§3.1–3.2; shared 3D map and progressive update |
| 2026-10-02 | [Weave Forcing](https://arxiv.org/abs/2610.03510v1) | Attention-cache States | — | [PDF p.3](https://arxiv.org/pdf/2610.03510v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03510v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03510v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.03510v1#page=6)；§3.2–3.3; query-weighted KV compression |
| 2026-10-02 | [In-Distribution Forcing](https://arxiv.org/abs/2610.03120v2) | Attention-cache States | — | [PDF p.3](https://arxiv.org/pdf/2610.03120v2#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03120v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03120v2#page=5)；§4; Self-Caching |
| 2026-10-02 | [Custom Forcing](https://arxiv.org/abs/2610.02914v2) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2610.02914v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02914v2#page=5)；§3.2–3.3; persistent reference KV |
| 2026-10-02 | [TRAC](https://arxiv.org/abs/2610.02779v1) | Attention-cache States | — | [PDF p.3](https://arxiv.org/pdf/2610.02779v1#page=3), [PDF p.6](https://arxiv.org/pdf/2610.02779v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02779v1#page=7)；§3.2.3; Eq. (13) |
| 2026-10-01 | [Spatial Memory Intelligence (SMI)](https://arxiv.org/abs/2610.02521v1) | Carrier-agnostic Visual Memory Management | — | [PDF p.5](https://arxiv.org/pdf/2610.02521v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02521v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02521v1#page=7)；§3.1–3.4; Eqs. (2)–(11) |
| 2026-10-01 | [World Observer](https://arxiv.org/abs/2610.02162v1) | VAE-space Visual Memory | — | [PDF p.4](https://arxiv.org/pdf/2610.02162v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02162v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02162v1#page=6)；§3; §3.2; observer sink |
| 2026-10-01 | [MosaiChunk](https://arxiv.org/abs/2610.02153v1) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2610.02153v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02153v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)；§3.1–3.2; §4 |
| 2026-09-30 | [Memorizon](https://arxiv.org/abs/2610.00544v1) | VAE-space Visual Memory | — | [PDF p.4](https://arxiv.org/pdf/2610.00544v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00544v1#page=5)；§3.2–3.3; bounded union bank |
| 2026-09-30 | [LOCI](https://arxiv.org/abs/2609.40222v1) | Recurrent and State-space States | — | [PDF p.4](https://arxiv.org/pdf/2609.40222v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.40222v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.40222v1#page=6)；§4; hybrid KDA/softmax and chunk updates |
| 2026-09-30 | [DeCoPrune](https://arxiv.org/abs/2609.39096v2) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.39096v2#page=6)；§3.1–3.2; Eqs. (1), (2); CMBench |
| 2026-09-30 | [FrameMorrow](https://arxiv.org/abs/2609.38839v1) | Pixel-space Visual Memory | — | [PDF p.4](https://arxiv.org/pdf/2609.38839v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38839v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38839v1#page=6)；§3; Eq. (9) |
| 2026-09-29 | [Self-Aligned Forcing (SAF)](https://arxiv.org/abs/2609.38114v1) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.38114v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38114v1#page=5)；§3.1–3.2; differentiable noisy history |
| 2026-09-29 | [Honeycomb](https://arxiv.org/abs/2609.37690v2) | Spatial and Geometric States | — | [PDF p.4](https://arxiv.org/pdf/2609.37690v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37690v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.37690v2#page=6)；§3.2–3.4; six spatial/spatiotemporal planes |
| 2026-09-28 | [Compress to Remember (PACC)](https://arxiv.org/abs/2609.36364v1) | Encoded History States | — | [PDF p.3](https://arxiv.org/pdf/2609.36364v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.36364v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.36364v1#page=5)；§3; Eq. (1); on-policy prediction matching |
| 2026-09-28 | [Geometry as Address (GEAR)](https://arxiv.org/abs/2609.34722v1) | VAE-space Visual Memory | Explicit State | [PDF p.3](https://arxiv.org/pdf/2609.34722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34722v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34722v1#page=5)；§3.1–3.3; visual bank; Invisible Octree |
| 2026-09-28 | [WorldAttention](https://arxiv.org/abs/2609.34606v1) | Attention-cache States | — | [PDF p.3](https://arxiv.org/pdf/2609.34606v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34606v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34606v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.34606v1#page=6)；§3.1–3.2; hierarchical cache; HSA |
| 2026-09-26 | [In-Flight KV Cache (FlashForward)](https://arxiv.org/abs/2609.32540v2) | Attention-cache States | — | [PDF p.5](https://arxiv.org/pdf/2609.32540v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.32540v2#page=6)；§3.1; stage-specific banks Bk |
| 2026-09-22 | [QuantWM](https://arxiv.org/abs/2609.26425v3) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.26425v3#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26425v3#page=5), [PDF p.7](https://arxiv.org/pdf/2609.26425v3#page=7)；§4; residual KV quantization and correction |
| 2026-09-18 | [ZYT-World](https://arxiv.org/abs/2609.21712v2) | VAE-space Visual Memory | — | [PDF p.3](https://arxiv.org/pdf/2609.21712v2#page=3), [PDF p.10](https://arxiv.org/pdf/2609.21712v2#page=10)；§3.6; four retrieved memory latents |
| 2026-09-17 | [Recency Forcing](https://arxiv.org/abs/2609.19729v1) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.19729v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.19729v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.19729v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.19729v1#page=7)；§4; TRB and BAR |
| 2026-09-13 | [AlayaVista](https://arxiv.org/abs/2609.14462v1) | Attention-cache States | — | [PDF p.5](https://arxiv.org/pdf/2609.14462v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.14462v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.14462v1#page=7)；§3.3; Chunk-causal state evolution |
| 2026-09-10 | [World in World (WiW)](https://arxiv.org/abs/2609.11548v1) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.11548v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11548v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11548v1#page=7)；§3.4; clean per-layer KV archive |
| 2026-09-10 | [Uncertainty DMD](https://arxiv.org/abs/2609.11265v1) | Attention-cache States | — | [PDF p.4](https://arxiv.org/pdf/2609.11265v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.11265v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.11265v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11265v1#page=7)；§4.2–4.3; Algorithm 1, line 16 |

### 逐篇分类理由与五个视角

#### WorldCast — 2610.12412

- **论文/日期**：[WorldCast: Distributed Multiplayer World Models](https://arxiv.org/abs/2610.12412v1)；首次 2026-10-08，所核对版本 `2610.12412v1`，修订 2026-10-08。
- **Forms**：VAE-space Visual Memory；同时 Explicit State。共享 scene bank 保存 latent、pose、depth；另有离开视野后的玩家状态跟踪，支持显式副分类。
- **Functions / Operations**：分布式多玩家的世界与离屏玩家状态；共享场景检索；缺失覆盖补充；冗余撤回；玩家状态更新。
- **Learning / Evaluation**：分布式生成与场景共享训练；多玩家视角、遮挡及分布式一致性。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.12412v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12412v1#page=5)；§3.2–3.3; player state and scene bank。

#### Memory Forcing — 2610.11756

- **论文/日期**：[Memory Forcing: Attendable Mid-Horizon History for Streaming Video Generation](https://arxiv.org/abs/2610.11756v1)；首次 2026-10-08，所核对版本 `2610.11756v1`，修订 2026-10-08。
- **Forms**：Attention-cache States。工作区之外保留中期历史 K/V，按内容多样性管理 archive bank；与 2510.03198 的 Minecraft Memory Forcing 是不同论文。
- **Functions / Operations**：中期内容与主体外观；工作 bank / archive bank；预算分配、选择与位置编码。
- **Learning / Evaluation**：论文提出的流式推理缓存策略；长视频质量、历史可访问性与缓存预算消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2610.11756v1#page=3), [PDF p.5](https://arxiv.org/pdf/2610.11756v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.11756v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.11756v1#page=7)；§3.3; Algorithm 1; bank-aware RoPE。

#### SGF+ — 2610.10429

- **论文/日期**：[SGF+: Decoupling Gradient Flows for Autoregressive Video Generation](https://arxiv.org/abs/2610.10429v2)；首次 2026-10-07，所核对版本 `2610.10429v2`，修订 2026-10-08。
- **Forms**：Attention-cache States。跨段信息载体是 context K/V；context writer 与 denoiser 的参数在离线训练中分离，不是实例级参数记忆。
- **Functions / Operations**：长时外推中的上下文可用性；clean-context 写入与噪声目标读取。
- **Learning / Evaluation**：重构可微上下文路径；分离 writer/denoiser 梯度；短训练窗到 60/240 秒外推；VBench / MovieGen prompts。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.10429v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.10429v2#page=5), [PDF p.6](https://arxiv.org/pdf/2610.10429v2#page=6)；§3.1–3.3; Eqs. (1), (2), (5)。

#### SPW-Nav — 2610.08941

- **论文/日期**：[SPW-Nav: A Streaming Panoramic World Model for Language-Guided Navigation](https://arxiv.org/abs/2610.08941v1)；首次 2026-10-06，所核对版本 `2610.08941v1`，修订 2026-10-06。
- **Forms**：VAE-space Visual Memory。保存不同时间尺度的历史 latent 与首帧锚点；当前 ERP 全景观测不等于持久度量地图。
- **Functions / Operations**：导航中的空间与视角连续性；多尺度 patchify 与历史打包。
- **Learning / Evaluation**：流式全景生成和导航模块训练；全景生成、导航任务及记忆消融。
- **核对出处**：[PDF p.5](https://arxiv.org/pdf/2610.08941v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.08941v1#page=6)；§4.4; multi-scale memory compression。

#### Keepsake — 2610.06588

- **论文/日期**：[Keepsake: Selective Spatial Memory for Long-Horizon Video Generation](https://arxiv.org/abs/2610.06588v1)；首次 2026-10-05，所核对版本 `2610.06588v1`，修订 2026-10-05。
- **Forms**：Carrier-agnostic Visual Memory Management。记忆是宿主的观测 bank；image/latent 实现依宿主而变。pose–appearance graph 是每次更新的冗余统计，不是永久 3D 世界模型。
- **Functions / Operations**：固定预算下的重访外观与空间覆盖；合并旧观测与新观测；关系冗余评分；逐项淘汰。
- **Learning / Evaluation**：无需新增生成器训练的保留策略；MemCam / WorldMem；固定预算、重访、损坏记忆消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.06588v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.06588v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.06588v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.06588v1#page=7)；§3.1–3.3; Algorithm 1; §4.1。

#### HLA-WM — 2610.05739

- **论文/日期**：[HLA-WM: Hybrid Linear Attention for Long-Horizon Video World Models](https://arxiv.org/abs/2610.05739v1)；首次 2026-10-05，所核对版本 `2610.05739v1`，修订 2026-10-05。
- **Forms**：Recurrent and State-space States。主载体是可重组的线性注意力状态；选中片段另有 softmax K/V，同属 Implicit State 的混合子类。
- **Functions / Operations**：长时空间一致性和细节；片段仿射摘要、几何检索、递归状态重组。
- **Learning / Evaluation**：training-free；冻结已有 SANA-WM AR generator，检索与重组历史状态；长时相机轨迹、重访及状态重组消融。
- **核对出处**：[PDF p.1](https://arxiv.org/pdf/2610.05739v1#page=1), [PDF p.5](https://arxiv.org/pdf/2610.05739v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.05739v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.05739v1#page=7)；§4.2–4.4; affine summaries and state recomposition。

#### Artemis — 2610.07031

- **论文/日期**：[Artemis: Geometry-Grounded Multi-Agent Driving World Models with Shared 3D State and Progressive Memory Update](https://arxiv.org/abs/2610.07031v1)；首次 2026-10-04，所核对版本 `2610.07031v1`，修订 2026-10-04。
- **Forms**：Spatial and Geometric States；同时 Implicit State。多主体共享的 3D 地图及代理位置由 rollout 关键帧逐步更新；另有生成器历史缓存。
- **Functions / Operations**：多视角、遮挡主体和背景动态；重建共享地图；几何投影；关键帧渐进更新。
- **Learning / Evaluation**：几何条件化多主体视频模型训练；MA-CARLA、多视角一致性及地图更新消融。
- **核对出处**：[PDF p.5](https://arxiv.org/pdf/2610.07031v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.07031v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.07031v1#page=7)；§3.1–3.2; shared 3D map and progressive update。

#### Weave Forcing — 2610.03510

- **论文/日期**：[Weave Forcing: Compositional Memory Routing for Interactive Long Video Generation](https://arxiv.org/abs/2610.03510v1)；首次 2026-10-02，所核对版本 `2610.03510v1`，修订 2026-10-02。
- **Forms**：Attention-cache States。LLM 把语义 slot 路由到历史镜头，但实际读取的是压缩 K/V；瞬时路由标签不构成持久实体状态。
- **Functions / Operations**：多主体及场景的组合一致性；slot 路由、查询加权 K/V、分组注意力与初始化。
- **Learning / Evaluation**：训练外的组合记忆路由；交互式提示切换、多主体组合及预算消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2610.03510v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03510v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03510v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.03510v1#page=6)；§3.2–3.3; query-weighted KV compression。

#### In-Distribution Forcing — 2610.03120

- **论文/日期**：[In-Distribution Forcing for Long Video Generation at Test Time](https://arxiv.org/abs/2610.03120v2)；首次 2026-10-02，所核对版本 `2610.03120v2`，修订 2026-10-07。
- **Forms**：Attention-cache States。修改历史 K/V 的生成及缓存分布，以改善测试时长视频外推；没有实例级参数更新。
- **Functions / Operations**：长时外观与分布稳定性；Self-Caching；保留与重用模型原生历史缓存。
- **Learning / Evaluation**：测试时策略；沿用预训练模型；长视频外推及分布失配分析。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2610.03120v2#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03120v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03120v2#page=5)；§4; Self-Caching。

#### Custom Forcing — 2610.02914

- **论文/日期**：[Custom Forcing: Training-Free Subject Customization for Autoregressive Video Generation](https://arxiv.org/abs/2610.02914v2)；首次 2026-10-02，所核对版本 `2610.02914v2`，修订 2026-10-05。
- **Forms**：Attention-cache States。主体参考与自定义锚点编码为可复用 K/V；customization 是训练外条件注入，不是 Parametric Memory。
- **Functions / Operations**：自定义主体身份与外观；一次编码参考缓存；锚点引导和位置调节。
- **Learning / Evaluation**：training-free；主体定制、长时身份保持及锚点消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.02914v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02914v2#page=5)；§3.2–3.3; persistent reference KV。

#### TRAC — 2610.02779

- **论文/日期**：[TRAC: Trajectory-aware Reuse and Adaptive Correction for Efficient Autoregressive Video Generation](https://arxiv.org/abs/2610.02779v1)；首次 2026-10-02，所核对版本 `2610.02779v1`，修订 2026-10-02。
- **Forms**：Attention-cache States。结构校正查询首个 chunk 的缓存 K/V；频谱处理对象与原始历史帧库应区分。
- **Functions / Operations**：加速时的长期结构稳定性；轨迹感知复用；首段 K/V 池化查询及校正。
- **Learning / Evaluation**：训练外推理加速；速度/质量及首段长期锚点消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2610.02779v1#page=3), [PDF p.6](https://arxiv.org/pdf/2610.02779v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02779v1#page=7)；§3.2.3; Eq. (13)。

#### Spatial Memory Intelligence (SMI) — 2610.02521

- **论文/日期**：[Spatial Memory Intelligence: Endowing World Models with Understanding-Driven Long-Term Memory](https://arxiv.org/abs/2610.02521v1)；首次 2026-10-01，所核对版本 `2610.02521v1`，修订 2026-10-01。
- **Forms**：Carrier-agnostic Visual Memory Management。显式定义 bank 项为保留的视频 chunk，按宿主编码后供生成器读取；训练 MLLM 管理器不等于把本次轨迹写进参数。
- **Functions / Operations**：空间覆盖、物体变化及可靠观测；聚类、簇内稀疏化、动作感知检索、可靠性过滤。
- **Learning / Evaluation**：原子操作标注与 Qwen3.5 管理器 SFT；WorldPlay-1.5 宿主、长时生成和四项操作消融。
- **核对出处**：[PDF p.5](https://arxiv.org/pdf/2610.02521v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02521v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02521v1#page=7)；§3.1–3.4; Eqs. (2)–(11)。

#### World Observer — 2610.02162

- **论文/日期**：[World Observer: Joint Actor-Observer Generation for Persistent World Modeling](https://arxiv.org/abs/2610.02162v1)；首次 2026-10-01，所核对版本 `2610.02162v1`，修订 2026-10-01。
- **Forms**：VAE-space Visual Memory。actor/observer 的 latent 历史及 observer sink 提供超出 actor 视野的视觉证据；没有独立持久 3D 地图。
- **Functions / Operations**：不可见区域与场景持续性；联合 actor/observer 生成；保留 observer 条件。
- **Learning / Evaluation**：联合生成与观测视角训练；重访和持续世界建模、observer 消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.02162v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02162v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02162v1#page=6)；§3; §3.2; observer sink。

#### MosaiChunk — 2610.02153

- **论文/日期**：[MosaiChunk: Compositing Spatio-Temporal Memory for Autoregressive Video Generation](https://arxiv.org/abs/2610.02153v1)；首次 2026-10-01，所核对版本 `2610.02153v1`，修订 2026-10-01。
- **Forms**：Attention-cache States。从历史 chunk 中选择局部 K/V section 并拼成远期 memory；mosaic 指缓存拼接而不是像素拼图。
- **Functions / Operations**：离开窗口后的主体及场景细节；分区提取、top-N 路由、value 权重、缓存拼接。
- **Learning / Evaluation**：冻结 backbone 的 router 自蒸馏；RememBench：T2V 离开/重现及 I2V 相机重访。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.02153v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02153v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)；§3.1–3.2; §4。

#### Memorizon — 2610.00544

- **论文/日期**：[Memorizon: Training World Models Beyond Their Context Window](https://arxiv.org/abs/2610.00544v1)；首次 2026-09-30，所核对版本 `2610.00544v1`，修订 2026-09-30。
- **Forms**：VAE-space Visual Memory。按相机共视性检索观测对齐的历史 latent，联合 bank 有 kK 上界；几何是检索地址而非持久外观地图。
- **Functions / Operations**：远距离重访对应的视觉内容；top-K latent 检索；跨 scored chunks 合并 bank。
- **Learning / Evaluation**：稀疏历史条件下的长跨度监督；重访相关性、训练跨度和跨 episode 错记忆消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2610.00544v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00544v1#page=5)；§3.2–3.3; bounded union bank。

#### LOCI — 2609.40222

- **论文/日期**：[LOCI: Spatial Linear Memory for Streaming World Models](https://arxiv.org/abs/2609.40222v1)；首次 2026-09-30，所核对版本 `2609.40222v1`，修订 2026-09-30。
- **Forms**：Recurrent and State-space States。KDA 状态跨 chunk 保留历史，同时配合 bounded softmax context；相机位置编码本身不构成 Explicit State。
- **Functions / Operations**：流式场景结构与长时依赖；chunk-wise 递归写入；局部 softmax 读取。
- **Learning / Evaluation**：混合线性注意力与空间位置机制训练；流式世界生成、重访和注意力结构消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.40222v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.40222v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.40222v1#page=6)；§4; hybrid KDA/softmax and chunk updates。

#### DeCoPrune — 2609.39096

- **论文/日期**：[DeCoPrune: Efficient KV-Cache Pruning for Autoregressive Video Diffusion via Denoising Consistency](https://arxiv.org/abs/2609.39096v2)；首次 2026-09-30，所核对版本 `2609.39096v2`，修订 2026-10-05。
- **Forms**：Attention-cache States。基于去噪差异筛选历史 K/V token；记忆是被保留的缓存，不是打分用的临时特征。
- **Functions / Operations**：重现与重访时的历史内容；共享 token mask；去噪一致性评分及缓存裁剪。
- **Learning / Evaluation**：训练外裁剪；CMBench：58 episodes / 116 reappear-revisit tasks。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.39096v2#page=6)；§3.1–3.2; Eqs. (1), (2); CMBench。

#### FrameMorrow — 2609.38839

- **论文/日期**：[FrameMorrow: Future-guided Frame Selection with Prospective Tokens for Long-Horizon Video Generation](https://arxiv.org/abs/2609.38839v1)；首次 2026-09-30，所核对版本 `2609.38839v1`，修订 2026-09-30。
- **Forms**：Pixel-space Visual Memory。prospective tokens 用于选帧；回收后交给生成器的是历史帧，不能因学习了查询 token 就归为 Parametric Memory。
- **Functions / Operations**：未来片段需要的历史视觉细节；未来导向评分；选择历史帧；原生条件接口注入。
- **Learning / Evaluation**：未来/历史关系及 prospective tokens 的离线学习；长时生成、帧选择及未来查询消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.38839v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38839v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38839v1#page=6)；§3; Eq. (9)。

#### Self-Aligned Forcing (SAF) — 2609.38114

- **论文/日期**：[Self-Aligned Forcing: Streaming Video Diffusion with Differentiable Noisy History](https://arxiv.org/abs/2609.38114v1)；首次 2026-09-29，所核对版本 `2609.38114v1`，修订 2026-09-29。
- **Forms**：Attention-cache States。跨段保留与当前去噪阶段对齐的 noisy-history K/V，辅以 clean sink；不是仅在同一段内部复用计算。
- **Functions / Operations**：流式历史的噪声阶段一致性；stage-aligned history；clean sink；recache/pipeline。
- **Learning / Evaluation**：可微噪声历史的 self-aligned training；流式质量、历史噪声阶段及速度消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.38114v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38114v1#page=5)；§3.1–3.2; differentiable noisy history。

#### Honeycomb — 2609.37690

- **论文/日期**：[Honeycomb: Constant-Size Scene Memory Representation for Video World Models](https://arxiv.org/abs/2609.37690v2)；首次 2026-09-29，所核对版本 `2609.37690v2`，修订 2026-09-30。
- **Forms**：Spatial and Geometric States。六个显式坐标平面承载历史特征并按空间地址写读；特征是学习得到的也不改变几何载体分类。
- **Functions / Operations**：恒定大小场景与动态记忆；坐标对齐写入；投影读取；warp/fusion 与置信度。
- **Learning / Evaluation**：场景记忆表示及生成器联合训练；长期空间一致性、容量和融合消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.37690v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37690v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.37690v2#page=6)；§3.2–3.4; six spatial/spatiotemporal planes。

#### Compress to Remember (PACC) — 2609.36364

- **论文/日期**：[Compress to Remember: Learning Compact Memory via On-Policy Distillation for Long Video Generation](https://arxiv.org/abs/2609.36364v1)；首次 2026-09-28，所核对版本 `2609.36364v1`，修订 2026-09-28。
- **Forms**：Encoded History States。历史前缀压缩为更少的 learned query embeddings；跨帧混合而不直接观测对齐。query 数与 prefix/压缩设置有关，不声称全历史恒定长度；compressor 离线训练不是实例参数记忆。
- **Functions / Operations**：压缩预算下的长期视觉内容；前缀编码为紧凑 memory tokens；条件读取。
- **Learning / Evaluation**：冻结生成器的 on-policy distillation；长视频一致性、token 预算与压缩训练消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2609.36364v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.36364v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.36364v1#page=5)；§3; Eq. (1); on-policy prediction matching。

#### Geometry as Address (GEAR) — 2609.34722

- **论文/日期**：[Geometry as Address: Routing Attention to Visual Memory for Long-Horizon Camera-Controlled Video Generation](https://arxiv.org/abs/2609.34722v1)；首次 2026-09-28，所核对版本 `2609.34722v1`，修订 2026-09-28。
- **Forms**：VAE-space Visual Memory；同时 Explicit State。主 bank 保存 (latent, camera)；额外持久 Invisible Octree 记录可见性证据。显式副载体仅指可见性，不夸大为全外观 3D 地图。
- **Functions / Operations**：场景重访与可见区域覆盖；几何地址检索；可见性写入；历史 attention routing。
- **Learning / Evaluation**：生成/记忆路由训练；长时相机控制、重访和几何地址消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2609.34722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34722v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34722v1#page=5)；§3.1–3.3; visual bank; Invisible Octree。

#### WorldAttention — 2609.34606

- **论文/日期**：[WorldAttention: An Efficient Attention Architecture for Interactive Video World Models](https://arxiv.org/abs/2609.34606v1)；首次 2026-09-28，所核对版本 `2609.34606v1`，修订 2026-09-28。
- **Forms**：Attention-cache States。历史 K/V 分页跨 GPU/CPU/NVMe 存储并按需加载；主载体是缓存，linear attention 分支不足以单独证明跨 rollout 状态记忆。
- **Functions / Operations**：低成本访问长历史；分页、卸载、分级检索；稀疏/线性混合读取。
- **Learning / Evaluation**：注意力结构与系统实现；交互式长时生成、缓存规模和吞吐分析。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2609.34606v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34606v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34606v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.34606v1#page=6)；§3.1–3.2; hierarchical cache; HSA。

#### In-Flight KV Cache (FlashForward) — 2609.32540

- **论文/日期**：[In-Flight KV Cache with Clean Anchors for Faster Autoregressive Video Diffusion](https://arxiv.org/abs/2609.32540v2)；首次 2026-09-26，所核对版本 `2609.32540v2`，修订 2026-09-30。
- **Forms**：Attention-cache States。不同去噪阶段的 K/V bank 跨 chunk 复用；clean anchors 包含前瞻规划信息，应区分输出按序与输入严格因果。
- **Functions / Operations**：加速时的跨段连续性；阶段对应 bank；稀疏 clean anchors；流水线。
- **Learning / Evaluation**：推理期缓存调度；速度/质量与 stage/anchor 消融。
- **核对出处**：[PDF p.5](https://arxiv.org/pdf/2609.32540v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.32540v2#page=6)；§3.1; stage-specific banks Bk。

- **Scope 边界**：AR renderer 条件于预先生成的双侧 anchors；不得表述为无未来条件的严格在线 causal 生成。

#### QuantWM — 2609.26425

- **论文/日期**：[QuantWM: Temporally Consistent 2-Bit KV Cache Quantization for Video World Models](https://arxiv.org/abs/2609.26425v3)；首次 2026-09-22，所核对版本 `2609.26425v3`，修订 2026-09-28。
- **Forms**：Attention-cache States。保存低位宽历史 K/V 与校正信息；量化和注意力偏差修复不是经验写入模型权重。
- **Functions / Operations**：压缩后的时序与外观一致性；残差量化；key centroid / 主方向修正。
- **Learning / Evaluation**：缓存量化与校正策略；2-bit KV 长时生成、位宽及时间一致性消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.26425v3#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26425v3#page=5), [PDF p.7](https://arxiv.org/pdf/2609.26425v3#page=7)；§4; residual KV quantization and correction。

#### ZYT-World — 2609.21712

- **论文/日期**：[ZYT-World: A Real-Time Controllable World Model for Closed-Loop Autonomous-Driving Simulation](https://arxiv.org/abs/2609.21712v2)；首次 2026-09-18，所核对版本 `2609.21712v2`，修订 2026-09-22。
- **Forms**：VAE-space Visual Memory。名为 implicit memory 的模块检索 3 个空间及 1 个时间历史 latent，再经 residual cross-attention 注入；载体仍是观测对齐 latent。
- **Functions / Operations**：闭环驾驶的时空连续性；空间/时间检索；四帧 latent；cross-attention。
- **Learning / Evaluation**：驾驶世界模型及 memory injection 训练；闭环驾驶、多源控制及记忆检索消融。
- **核对出处**：[PDF p.3](https://arxiv.org/pdf/2609.21712v2#page=3), [PDF p.10](https://arxiv.org/pdf/2609.21712v2#page=10)；§3.6; four retrieved memory latents。

#### Recency Forcing — 2609.19729

- **论文/日期**：[Recency Forcing: Bridging the Long-Horizon Gap in Autoregressive Video Generation](https://arxiv.org/abs/2609.19729v1)；首次 2026-09-17，所核对版本 `2609.19729v1`，修订 2026-09-17。
- **Forms**：Attention-cache States。推理时仍使用历史 K/V，贡献在训练/测试淘汰及读取偏差对齐；归入缓存策略/学习而非新参数载体。
- **Functions / Operations**：窗口外推时的长时稳定性；TRB/BAR 处理 recency 与缓存淘汰失配。
- **Learning / Evaluation**：训练配方与缓存读取偏差对齐；长视频外推和训练/推理失配消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.19729v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.19729v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.19729v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.19729v1#page=7)；§4; TRB and BAR。

#### AlayaVista — 2609.14462

- **论文/日期**：[AlayaVista: Streaming World Modeling from Panoramic States to Perspective Video](https://arxiv.org/abs/2609.14462v1)；首次 2026-09-13，所核对版本 `2609.14462v1`，修订 2026-09-13。
- **Forms**：Attention-cache States。跨 AR chunk 保留并读取的是全景特征的 K/V。当前全景 latent 供 perspective renderer 使用，不等于跨 chunk 的持久 VAE bank；据实际历史读取路径改归 Attention-cache。
- **Functions / Operations**：全景/透视世界及视角连续性；chunk-causal 全景 K/V 写读；当前全景 latent 的 viewport rendering。
- **Learning / Evaluation**：全景到透视流式生成训练；持续世界与相机轨迹、多视角一致性。
- **核对出处**：[PDF p.5](https://arxiv.org/pdf/2609.14462v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.14462v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.14462v1#page=7)；§3.3; Chunk-causal state evolution。

- **Scope 边界**：跨 chunk 历史由全景 K/V 承载；未建立大位移下的全局持久空间记忆，也不当作独立历史 latent archive。

#### World in World (WiW) — 2609.11548

- **论文/日期**：[World in World: Explore the World with World Models](https://arxiv.org/abs/2609.11548v1)；首次 2026-09-10，所核对版本 `2609.11548v1`，修订 2026-09-10。
- **Forms**：Attention-cache States。memory bank 归档被淘汰片段的逐层 clean K/V，附 pose/time；不能将 clean visual state 直接理解为像素或 VAE bank。
- **Functions / Operations**：探索、动作与历史场景连续性；归档 finalized K/V；姿态/时间路由；有限预算读取。
- **Learning / Evaluation**：世界内探索与动作条件生成训练；探索任务、历史访问及 cache 消融。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.11548v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11548v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11548v1#page=7)；§3.4; clean per-layer KV archive。

#### Uncertainty DMD — 2609.11265

- **论文/日期**：[Uncertainty DMD: Restoring Diversity in Few-Step Autoregressive Video Distillation](https://arxiv.org/abs/2609.11265v1)；首次 2026-09-10，所核对版本 `2609.11265v1`，修订 2026-09-10。
- **Forms**：Attention-cache States。每个 chunk 在写入时可扰动一次，再经 KV encoder 写入递归缓存，之后固定供后续读取；是跨段记忆写入操作，不只是单段去噪复用。
- **Functions / Operations**：历史条件中的多样性与持续动态；stochastic cache writing；固定写入后读取；首段 timestep perturbation。
- **Learning / Evaluation**：DMD curriculum，训练/推理使用相同写入规则；cache transplantation、diversity decomposition 及写入消融；实验主要是 5 秒，未证明分钟级记忆。
- **核对出处**：[PDF p.4](https://arxiv.org/pdf/2609.11265v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.11265v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.11265v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11265v1#page=7)；§4.2–4.3; Algorithm 1, line 16。

## Benchmark 核对

| 条目 | 分类 | 历史必要性 | 协议和出处 |
|---|---|---|---|
| [RememBench](https://arxiv.org/abs/2610.02153v1) | Memory-oriented Benchmarks | required | 离开 active window 后的 T2V 重现与 I2V 相机重访；测试历史内容恢复。 [§4; PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6) |
| [CMBench](https://arxiv.org/abs/2609.39096v2) | Memory-oriented Benchmarks | required | 58 episodes / 116 tasks；Reappear 与 Revisit 对已见内容提出历史依赖。 [§3.2 (continues p.6); PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5) |
| [OPIS](https://arxiv.org/abs/2609.35052v1) | Memory-oriented Benchmarks | subset | 从初始输入建立 object inventory，Presence/Identity/Structure 读出；历史依赖涉及重现等子集，不能宣称全部 case 都需窗口外记忆。 [§3.1; §4 (p.5); PDF p.4](https://arxiv.org/pdf/2609.35052v1#page=4) |
| [StateBench](https://arxiv.org/abs/2609.03673v1) | Memory-oriented Benchmarks | required | 200 cases，包含可见历史、遮挡过程和复杂状态转移；揭示边界测试状态续接。 [§3.1; Figure 2 (p.4); PDF p.5](https://arxiv.org/pdf/2609.03673v1#page=5) |

`required`：协议直接要求恢复已见/隐藏历史；`subset`：部分 case 涉及历史，整套不能都当成记忆专用；`proxy`：长序列任务表现是间接指标。同一论文的 method 与 benchmark 条目按不同角色登记，不算两篇新论文。

## 训练与诊断研究

| 论文 | 视角 | 核对结论 | 原文出处 |
|---|---|---|---|
| [Connected Self Forcing: Beyond Local Learning in Video Autoregression](https://arxiv.org/abs/2610.12156v1) | Learning | 通过重放恢复跨生成 latent / KV writer 的梯度路径；推理记忆载体继承原生缓存，贡献主要在 Learning。 | [PDF p.4](https://arxiv.org/pdf/2610.12156v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12156v1#page=5)；§3; shortcut replay |
| [Does Video Memory Use What It Retrieves? A Causal Audit of Memory Specificity](https://arxiv.org/abs/2609.12090v1) | Evaluation | 仅收录 WorldMem AR generative arm 的 read-time 历史内容替换实验，衡量 episode-specific 内容是否必要。JEPA / SAM2 等子研究不作为 AR video memory 证据。 | [PDF p.5](https://arxiv.org/pdf/2609.12090v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.12090v1#page=7)；§4.2; §5.5; Figure 3 (WorldMem arm) |

## 已有条目：不重复新增

此表核对原有条目的载体和元数据。本轮严格 scope 判定针对本次新增，原有条目保持基线；此表不代表所有历史条目均通过同等 scope 复核。尤其可编程引擎类旧条目仍需另行核实 AR generator 的 memory 接口。

| 论文 | 当前分类 | 核对结论及出处 |
|---|---|---|
| [WorldCrafter: Consistent Video World Model with Implicit 3D-aware Memory](https://arxiv.org/abs/2609.24984v1) | Encoded History States | 历史 latent 经 3D-aware encoder 和 readout 转为固定 tokens；维持现有 Encoded History 分类，不重复新增。 [PDF p.3](https://arxiv.org/pdf/2609.24984v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.24984v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.24984v1#page=5)；§3; memory encoder/readout |
| [ConsistWorld: Evidence Routing for Consistent Multi-Agent World Models](https://arxiv.org/abs/2609.22641v1) | VAE-space Visual Memory | 共享已提交的历史 chunks 并进行 pose-conditioned 检索；維持现有 Visual 分类。 [PDF p.3](https://arxiv.org/pdf/2609.22641v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.22641v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.22641v1#page=5)；§3; committed history and pose-conditioned retrieval |
| [PhysStream: Streaming Physics-Grounded Video Generation with Structured Scene Memory and Fine-Grained Motion Control](https://arxiv.org/abs/2609.17521v2) | Spatial and Geometric States | 结构场景和运动控制维持跨段世界状态；仓库已有，保持 Explicit 分类。 [PDF p.4](https://arxiv.org/pdf/2609.17521v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.17521v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.17521v2#page=6)；§3; structured scene memory |
| [Programmable World Model](https://arxiv.org/abs/2609.10540v1) | Entity-centric States | 持久实体身份、语义与动态状态由可执行引擎维护；仓库已收录。 [PDF p.4](https://arxiv.org/pdf/2609.10540v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.10540v1#page=5)；entity-level OBB state; programmable engine |
| [OctWorld: Long-Range World-Consistent Video Generation with Octree-Based 3D Mapping](https://arxiv.org/abs/2609.03919v1) | Spatial and Geometric States | 生成 RGB-D 逐段融合至动态 octree TSDF，再投影为后续条件；仓库已收录。 [PDF p.4](https://arxiv.org/pdf/2609.03919v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.03919v1#page=5)；§3.1; OctMap |

本仓库 survey [The Past Frames the Future: Memory for Autoregressive Video Generation](https://arxiv.org/abs/2609.28466v1) 同样已在 News/Citation 中出现，不作新增方法。

## 暂不更新主列表的相关论文

以下逐篇给出筛除/暂缓理由。标为“摘要”的条目只完成元数据和摘要核对；正文核对过的边界项附页码。它们不是已证明与 memory 无关的全部论文，而是本次证据尚不支持放入主列表的候选。

| 首次提交 | 论文 | 核对级别 | 暂缓或范围判断 | 来源 |
|---|---|---|---|---|
| 2026-10-08 | [WorldGuide: Goal-Directed Video World Model for Procedural Task Execution](https://arxiv.org/abs/2610.12459v1) | 正文段落 | 程序规划与 bidirectional HunyuanVideo 执行器的系统；历史 latent conditioning 采用现有机制，不能据顺序任务执行将其列为 AR model memory 新方法。WorldGuide Bench 的任务顺序指标也移出。 | [PDF p.4](https://arxiv.org/pdf/2610.12459v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12459v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.12459v1#page=6)；§3.2–3.5 |
| 2026-10-08 | [Multi-Agent Egocentric World Model with Fine-Grained Embodied Interaction](https://arxiv.org/abs/2610.12299v1) | 正文段落 | 多主体整段 joint denoising 有共享历史图像池，但所核对方法未确立 chunk AR rollout；暂缓而不等同于 AR model memory。 | [PDF p.4](https://arxiv.org/pdf/2610.12299v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12299v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.12299v1#page=6)；§3.2–3.4 |
| 2026-10-08 | [Conditional Residual Prediction: Improving Autoregressive Video Diffusion without a Bidirectional Teacher](https://arxiv.org/abs/2610.11479v1) | 正文段落 | AR conditional residual prediction 聚焦短视频建模/蒸馏；未建立直接的跨步记忆设计或记忆专门评估，移出 Memory Learning 新增。 | [PDF p.4](https://arxiv.org/pdf/2610.11479v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.11479v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.11479v1#page=6)；§3.1–3.3 |
| 2026-10-08 | [Learning to Retrieve: Internalizing Memory Retrieval for Video World Models](https://arxiv.org/abs/2610.11444v1) | 正文段落 | GLA/GDN token 递归与 SANA-WM 宿主实验有依据，但所核对版本未明确给出跨 AR 生成 chunk 的 state 提交/读取规则。暂缓方法收录，保留为待核候选；不判定其无 memory。 | [PDF p.4](https://arxiv.org/pdf/2610.11444v1#page=4), [PDF p.6](https://arxiv.org/pdf/2610.11444v1#page=6), [PDF p.8](https://arxiv.org/pdf/2610.11444v1#page=8), [PDF p.13](https://arxiv.org/pdf/2610.11444v1#page=13)；§3.2; §4.1; Appendix A.1–A.2 |
| 2026-10-08 | [IntactWorld: Joint World Modeling with Intact Features](https://arxiv.org/abs/2610.11174v1) | 摘要 | 特征表示及 world/action joint modeling；摘要未给出超出活动上下文的持久载体。 | [arXiv 摘要](https://arxiv.org/abs/2610.11174v1) |
| 2026-10-07 | [Long-WAM: Scaling the Context of World-Action Models](https://arxiv.org/abs/2610.10528v1) | 摘要 | 长上下文 World-Action Model；主要用于想象/规划与动作，而非 decoded AR video 历史记忆。 | [arXiv 摘要](https://arxiv.org/abs/2610.10528v1) |
| 2026-10-07 | [MORCA: Offline-to-Online Reinforcement Learning for Adaptive Cache Reuse in Video Diffusion Acceleration](https://arxiv.org/abs/2610.10457v1) | 摘要 | 离线到在线 RL 调节扩散计算 cache reuse；不是逐步生成历史内容的 memory。 | [arXiv 摘要](https://arxiv.org/abs/2610.10457v1) |
| 2026-10-07 | [Real-Time Joint Audio-Video Generation by Parallel Adapter Composition](https://arxiv.org/abs/2610.10343v2) | 摘要 | 离线训练的并行音视频 adapters；adapter 的参数分离不证明经验特定参数记忆。 | [arXiv 摘要](https://arxiv.org/abs/2610.10343v2) |
| 2026-10-07 | [Beyond Masks and Trajectories: Flow-Guided Latent Action Injection for Stable Surgical Video Generation](https://arxiv.org/abs/2610.09800v1) | 摘要 | 手术视频的 flow-guided latent action 控制；未证明持久历史记忆。 | [arXiv 摘要](https://arxiv.org/abs/2610.09800v1) |
| 2026-10-06 | [World Models' Last Exam in Physics](https://arxiv.org/abs/2610.08791v1) | 摘要 | 综合物理评测；缺少历史必要性定义，暂不作为 memory benchmark。 | [arXiv 摘要](https://arxiv.org/abs/2610.08791v1) |
| 2026-10-06 | [CtrlCache: Accelerating Interactive Video World Models with Control-Aware Caching](https://arxiv.org/abs/2610.08777v1) | 摘要 | 控制感知 denoising 计算复用；加速缓存与窗口外历史记忆的贡献应分开。 | [arXiv 摘要](https://arxiv.org/abs/2610.08777v1) |
| 2026-10-05 | [Tracking Is Not Permanence: What Video World Models Keep of a Hidden Object](https://arxiv.org/abs/2610.07355v1) | 正文段落 | 主研究为 latent predictor 的物体持续性，Cosmos AR 仅为补充对照；移出以 AR video generator memory 为对象的诊断主列表。 | [PDF p.3](https://arxiv.org/pdf/2610.07355v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.07355v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.07355v1#page=5)；§3.1–3.4 |
| 2026-10-05 | [RealtimeWAM: One-Step Asynchronous World Action Models](https://arxiv.org/abs/2610.06617v1) | 摘要 | 一步异步 World-Action Model，主要输出/评估机器人策略。 | [arXiv 摘要](https://arxiv.org/abs/2610.06617v1) |
| 2026-10-04 | [FLEX-WAM: Flexible Block-Causal World-Action Models for Long-Horizon Imagination and Planning](https://arxiv.org/abs/2610.05483v1) | 摘要 | 灵活 block-causal WAM；机器人动作规划范围。 | [arXiv 摘要](https://arxiv.org/abs/2610.05483v1) |
| 2026-10-02 | [Kepler4D: Controllable Future Video Generation via 4D Scene State Evolution](https://arxiv.org/abs/2610.04152v1) | 正文段落 | 从观测构建 4D 状态并推演有限未来；有 Explicit State 候选，但未证明生成后跨轮写回，暂列 adjacent。 | [PDF p.4](https://arxiv.org/pdf/2610.04152v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.04152v1#page=5)；§3.2–3.4; 4D state and finite future controls |
| 2026-10-02 | [LoGo: Local-Global Rewards for Consistent Long-Horizon Video Generation](https://arxiv.org/abs/2610.03636v1) | 正文段落 | 几何一致性 RL 奖励与临时点云不是持久生成记忆；TrajectoryBench 整体是相机质量压力测试，未作为 AR memory 专门评测保留。 | [PDF p.3](https://arxiv.org/pdf/2610.03636v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03636v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03636v1#page=5)；§3; §4.1 |
| 2026-10-02 | [DuoMatching: Joint-Marginal Distribution Matching for Few-Step Video Generation](https://arxiv.org/abs/2610.03543v1) | 摘要 | few-step joint/marginal distillation；没有摘要级证据支持新 memory carrier。 | [arXiv 摘要](https://arxiv.org/abs/2610.03543v1) |
| 2026-10-02 | [Imagine the Future, Internalize the Gist: Efficient VLA Reasoning via Internalized Spatiotemporal Imagination](https://arxiv.org/abs/2610.02626v2) | 摘要 | VLA 的内部未来想象服务动作推理；不属于 decoded AR video memory 方法。 | [arXiv 摘要](https://arxiv.org/abs/2610.02626v2) |
| 2026-10-01 | [World Action Modeling with Progressive Visual Planning](https://arxiv.org/abs/2610.02508v1) | 摘要 | progressive visual planning 的 World-Action Model；动作执行范围。 | [arXiv 摘要](https://arxiv.org/abs/2610.02508v1) |
| 2026-10-01 | [A Simulation-Grounded Agentic VLM Framework for Wildfire Monitoring and Reporting](https://arxiv.org/abs/2610.02451v1) | 摘要 | 野火监测和报告的 VLM agent；不属于 AR 视频生成。 | [arXiv 摘要](https://arxiv.org/abs/2610.02451v1) |
| 2026-10-01 | [DMAD: Distribution Matching as Adversarial Distillation for Fast Visual Generation](https://arxiv.org/abs/2610.02188v1) | 摘要 | 通用视觉生成 adversarial distillation；不是历史记忆设计。 | [arXiv 摘要](https://arxiv.org/abs/2610.02188v1) |
| 2026-10-01 | [4Director: Controlling Video World Models with Rigid 3D Geometry](https://arxiv.org/abs/2610.02160v1) | 正文段落 | 刚性 3D 控制状态用于有限未来生成；跨生成轮持久写读尚未确立，候选 Explicit State。 | [PDF p.3](https://arxiv.org/pdf/2610.02160v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.02160v1#page=4)；rigid 3D state and controls |
| 2026-10-01 | [UniWAM: Unified World-Action Model](https://arxiv.org/abs/2610.02054v3) | 摘要 | 统一 World-Action Model；未证明与 AR 长视频历史记忆直接相符。 | [arXiv 摘要](https://arxiv.org/abs/2610.02054v3) |
| 2026-10-01 | [Memory-Guided B-Roll Generation from User Video Collections](https://arxiv.org/abs/2610.01884v1) | 正文段落 | collection/keyframe/transient anchors 属于 B-roll 外部生成工作流；独立 Gimg/Gvid 调用未证明 AR 视频生成器记忆。 | [PDF p.4](https://arxiv.org/pdf/2610.01884v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.01884v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.01884v1#page=6)；§3.1–3.3 |
| 2026-10-01 | [Oneira: From Open-Ended Generation to Open-World Interaction in Video World Models](https://arxiv.org/abs/2610.01614v1) | 正文段落 | 可执行世界状态属于 coding agent / engine；调用视频渲染器不证明 AR 视频模型的 memory。 | [PDF p.4](https://arxiv.org/pdf/2610.01614v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.01614v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.01614v1#page=6)；§3; engine and MiniMax renderer |
| 2026-10-01 | [Ego2Act: Evaluating Goal-Directed Manipulation in Egocentric Video Generation](https://arxiv.org/abs/2610.01092v1) | 摘要 | 目标导向操作评测；与记忆有关但摘要没有历史必要性协议，先列 related evaluation。 | [arXiv 摘要](https://arxiv.org/abs/2610.01092v1) |
| 2026-09-30 | [Video Generation Models: A Survey of Post-Training and Alignment](https://arxiv.org/abs/2610.00812v1) | 摘要 | 视频模型 post-training/alignment survey；作为背景文献，不列新方法。 | [arXiv 摘要](https://arxiv.org/abs/2610.00812v1) |
| 2026-09-30 | [JEPA-TTT: Persistent Test-Time Training of Latent World Models for Planning under Dynamics Shifts](https://arxiv.org/abs/2610.00722v1) | 正文段落 | 持续 test-time 更新 latent dynamics predictor；在更广义 world-model taxonomy 可归 Internal Parametric，但不进入本次 AR 视频主列表。 | [PDF p.3](https://arxiv.org/pdf/2610.00722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.00722v1#page=4)；persistent TTT of latent predictor |
| 2026-09-30 | [Physis-Lang: Self-Evolving Language as a Physical Representation for Video World Model](https://arxiv.org/abs/2609.40358v1) | 摘要 | 自演化语言作为物理描述/训练表达；未证明序列特定持续写读。 | [arXiv 摘要](https://arxiv.org/abs/2609.40358v1) |
| 2026-09-30 | [Enhancing Autoregressive Video Generation via Representation Adversarial Distillation](https://arxiv.org/abs/2609.40037v1) | 摘要 | representation adversarial distillation；相关训练研究，尚未正文核对其 memory 关系。 | [arXiv 摘要](https://arxiv.org/abs/2609.40037v1) |
| 2026-09-30 | [No Corners Cut: State-Grounded Transitions for Mid-Stream Prompt Switches in Video Generation](https://arxiv.org/abs/2609.38691v2) | 正文段落 | 最新帧状态驱动 prompt transition 与训练；不新增窗口外持久 bank。 | [PDF p.4](https://arxiv.org/pdf/2609.38691v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38691v2#page=5)；§3; state-grounded prompt transitions |
| 2026-09-29 | [LongTake: Learning to Sustain Dynamics in Long-Horizon Video Generation](https://arxiv.org/abs/2609.38562v1) | 正文段落 | 长 horizon teacher forcing / hybrid distillation，继承基线缓存；长视频训练本身不足以作为 memory 学习贡献。 | [PDF p.3](https://arxiv.org/pdf/2609.38562v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.38562v1#page=4)；§3–4 |
| 2026-09-29 | [HelixWorld: A Real-time Interactive Audio-Visual World Model](https://arxiv.org/abs/2609.38123v1) | 摘要 | 实时音视频基础模型；未核对到独立长时 memory 贡献，列 baseline。 | [arXiv 摘要](https://arxiv.org/abs/2609.38123v1) |
| 2026-09-29 | [Rollout-Marginal Distillation for Long-Horizon Autoregressive Video Generation](https://arxiv.org/abs/2609.37925v1) | 正文段落 | rollout-marginal 分布匹配及 refinement，继承历史接口；未直接改变/评估 memory 写读。 | [PDF p.3](https://arxiv.org/pdf/2609.37925v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.37925v1#page=4)；§3 |
| 2026-09-29 | [Complementary Retrieval-Augmented Prompting for Consistent Long-Form Video Generation](https://arxiv.org/abs/2609.37407v1) | 正文段落 | 外部 entity registry 与 keyframe retrieval 组成多镜头工作流；未确立 native AR video backbone 的跨 chunk 记忆路径。 | [PDF p.3](https://arxiv.org/pdf/2609.37407v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.37407v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37407v1#page=5)；§3; keyframe/entity workflow |
| 2026-09-29 | [Waypoint-1.5: A Real-Time Video World Model for Consumer Hardware](https://arxiv.org/abs/2609.37107v2) | 摘要 | 消费者硬件视频世界模型；列通用 baseline，未确认独立 memory 机制。 | [arXiv 摘要](https://arxiv.org/abs/2609.37107v2) |
| 2026-09-29 | [One from Infinity: Actualizing Futures from Pretrained World Models into Robot Actions](https://arxiv.org/abs/2609.36413v3) | 摘要 | 从预训练世界模型实际化未来为机器人动作；动作策略范围。 | [arXiv 摘要](https://arxiv.org/abs/2609.36413v3) |
| 2026-09-28 | [InfiniHand: Streaming World-Space Hand Motion Estimation from Egocentric Video](https://arxiv.org/abs/2609.35743v1) | 摘要 | 流式手部动作估计；不是视频生成。 | [arXiv 摘要](https://arxiv.org/abs/2609.35743v1) |
| 2026-09-28 | [GeoVerse: World-Consistent Novel View Synthesis in Geometric Latent Space](https://arxiv.org/abs/2609.35734v2) | 正文段落 | 几何 latent 的多轮新视角生成及点云融合；Wan/VACE 提供视觉 prior，不能等同于 AR video model memory。 | [PDF p.4](https://arxiv.org/pdf/2609.35734v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.35734v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.35734v2#page=6)；§3.1–3.2 |
| 2026-09-28 | [From Scores to Samples: Elastic Forcing for Autoregressive Video Generation](https://arxiv.org/abs/2609.35491v3) | 正文段落 | memory-efficient 是训练资源开销；sample-space MMD/replay 并非推理中的 episode memory。 | [PDF p.3](https://arxiv.org/pdf/2609.35491v3#page=3), [PDF p.4](https://arxiv.org/pdf/2609.35491v3#page=4)；§3 |
| 2026-09-28 | [WaveAlign: Cache-Aware Query-Row Scheduling for Sparse Attention in Long-Video Generation](https://arxiv.org/abs/2609.34814v1) | 摘要 | 稀疏 attention kernel/query-row 调度，关注硬件计算缓存；不新增内容记忆操作。 | [arXiv 摘要](https://arxiv.org/abs/2609.34814v1) |
| 2026-09-28 | [MaLiang-Harness: A Programmable Path to Image and Video Generation](https://arxiv.org/abs/2609.34309v1) | 摘要 | 可编程图像/视频 agent harness；摘要未确立 AR 历史载体。 | [arXiv 摘要](https://arxiv.org/abs/2609.34309v1) |
| 2026-09-28 | [WorldWeave: Growing Persistent Geometric Worlds for Video Generation](https://arxiv.org/abs/2609.34221v2) | 正文段落 | 世界几何先独立增长并提交，视频 query 只读渲染；生成 RGB 不写回 AR 视频历史。 | [PDF p.4](https://arxiv.org/pdf/2609.34221v2#page=4), [PDF p.6](https://arxiv.org/pdf/2609.34221v2#page=6)；§3; §3.5 Eq. (7) |
| 2026-09-27 | [StoryEngine: A State-Grounded Agentic Framework for Video Storytelling](https://arxiv.org/abs/2609.33627v1) | 正文段落 | agent 维护故事实体状态与参考库，再逐镜头调用生成器；未建立 AR 视频模型 memory。 | [PDF p.4](https://arxiv.org/pdf/2609.33627v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.33627v1#page=5)；§3.2 |
| 2026-09-26 | [UnStep: Training-Free Acceleration of Causal Video Diffusion with Fewer Steps Than Distillation](https://arxiv.org/abs/2609.32518v1) | 摘要 | 减少因果视频 denoising 步数；沿用窗口缓存，摘要未显示长时内容记忆贡献。 | [arXiv 摘要](https://arxiv.org/abs/2609.32518v1) |
| 2026-09-26 | [Carnator: Fast Text-to-Video Generation with Generation-Native Compatibility-Guided Cross-Request Reuse](https://arxiv.org/abs/2609.32420v1) | 摘要 | 跨用户请求的生成资产复用；不是同一条轨迹的历史记忆。 | [arXiv 摘要](https://arxiv.org/abs/2609.32420v1) |
| 2026-09-26 | [Devol-ONE: One Autoregressive Mixture of Transformers to Unify Vision-Language-Action and Latent World Modeling](https://arxiv.org/abs/2609.32193v2) | 摘要 | 统一 VLA 与 latent world modeling；缺少 decoded AR video memory 的证据。 | [arXiv 摘要](https://arxiv.org/abs/2609.32193v2) |
| 2026-09-25 | [TemplateCraft: Agentic Visual Template Generation](https://arxiv.org/abs/2609.31451v1) | 摘要 | 视觉模板 agent；process memory 不等于 AR 视频历史。 | [arXiv 摘要](https://arxiv.org/abs/2609.31451v1) |
| 2026-09-24 | [MVAgent: Multi-Agent Video Generation via Consistent Condition Construction and Shot-Level Policy Optimization](https://arxiv.org/abs/2609.30609v1) | 正文段落 | Orchestrator 的 continuity memory 与冻结 black-box shot generator；不是已确认的 AR backbone memory。 | [PDF p.2](https://arxiv.org/pdf/2609.30609v1#page=2), [PDF p.3](https://arxiv.org/pdf/2609.30609v1#page=3)；§2.1–2.4 |
| 2026-09-24 | [ViRDM: Taming Representation Distribution Matching for Few-Step Causal Video Generation](https://arxiv.org/abs/2609.28923v1) | 摘要 | few-step representation distribution matching；相关训练，未正文核对新增记忆机制。 | [arXiv 摘要](https://arxiv.org/abs/2609.28923v1) |
| 2026-09-23 | [DeltaWAM: Delta World Action Models for Bimanual Manipulation](https://arxiv.org/abs/2609.28811v1) | 摘要 | 双臂操作 World-Action Model；动作策略范围。 | [arXiv 摘要](https://arxiv.org/abs/2609.28811v1) |
| 2026-09-23 | [The Past Frames the Future: Memory for Autoregressive Video Generation](https://arxiv.org/abs/2609.28466v1) | 摘要 | 本仓库 survey 已收录；不是新增方法。 | [arXiv 摘要](https://arxiv.org/abs/2609.28466v1) |
| 2026-09-22 | [Code Plans, Diffusion Renders: Open-Ended Generative World Modeling](https://arxiv.org/abs/2609.26458v1) | 正文段落 | 执行代码世界与 MiniMax 视频渲染保留外观观测，但未明确 AR 生成器跨 chunk 的记忆接口；暂缓，不由系统级顺序生成推断 AR。 | [PDF p.4](https://arxiv.org/pdf/2609.26458v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26458v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.26458v1#page=6)；§3; observation registration |
| 2026-09-22 | [GameDirector: Decoupling Gameplay Logic from Rendering for Player-Configurable Game World Models](https://arxiv.org/abs/2609.25652v1) | 正文段落 | 生成器确实采用 AR/Causal Forcing++；新 HP/技能状态主要供 director 判定合法指令并构造 prompt。未证明它作为 AR generator 的新增历史记忆载体；不能因 AR backbone 就收录外部游戏逻辑。 | [PDF p.5](https://arxiv.org/pdf/2609.25652v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.25652v1#page=6)；§3.3–3.4 Eq. (6); §4.1 |
| 2026-09-21 | [Streaming Video Editing with Easy Adaptation](https://arxiv.org/abs/2609.24788v1) | 摘要 | 流式视频编辑 adaptation；编辑条件/离线参数适配不自动算 episode memory。 | [arXiv 摘要](https://arxiv.org/abs/2609.24788v1) |
| 2026-09-20 | [Grounded Action Model: 3D Grounding as a Foundation for Robotics](https://arxiv.org/abs/2609.23863v2) | 摘要 | 机器人 grounding/action 模型；不是 AR 视频生成历史。 | [arXiv 摘要](https://arxiv.org/abs/2609.23863v2) |
| 2026-09-19 | [PileBelief: Persistent Physical State for Interaction-Driven World Modeling](https://arxiv.org/abs/2609.22858v1) | 正文段落 | 挖掘交互中的 persistent physical belief，可类比 Explicit State；不以 decoded AR 视频生成为目标。 | [PDF p.3](https://arxiv.org/pdf/2609.22858v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.22858v1#page=4)；persistent physical belief |
| 2026-09-18 | [Sandwich-Residuals: Parameter-Efficient Test-time Adaptation of World Models](https://arxiv.org/abs/2609.21740v1) | 正文段落 | 测试时 residual 参数适应 world dynamics；广义可归 Modular Parametric，但未证明 AR 视频 rollout。 | [PDF p.3](https://arxiv.org/pdf/2609.21740v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.21740v1#page=4)；test-time residual adapters |
| 2026-09-17 | [Video DeltaNet: A Video-Native Hybrid Attention for Livestream Video Generation](https://arxiv.org/abs/2609.20744v3) | 正文段落 | 双向扫描在完整 clip 内处理过去/未来，且边界含最后帧；不能据此认定跨 AR rollout 的持久 recurrent state。 | [PDF p.3](https://arxiv.org/pdf/2609.20744v3#page=3), [PDF p.4](https://arxiv.org/pdf/2609.20744v3#page=4)；§2.1–2.2; bidirectional full-clip attention |
| 2026-09-17 | [Astronex-World 1.0: Real-Time Interactive World Model Foundation](https://arxiv.org/abs/2609.20034v1) | 正文段落 | 通用交互式基础模型；正文描述 sink + local KV，但不是独立新记忆贡献，列 baseline。 | [PDF p.4](https://arxiv.org/pdf/2609.20034v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.20034v1#page=6)；model architecture and causal rollout |
| 2026-09-16 | [vidax: A Unified JAX Framework for Video Generative Models on Accelerator Meshes](https://arxiv.org/abs/2609.18077v1) | 摘要 | JAX 训练/推理框架；不属于内容记忆方法。 | [arXiv 摘要](https://arxiv.org/abs/2609.18077v1) |
| 2026-09-14 | [LynnReal-Omni: Native multi-modal Video Generation for Agentic Visual Workflows](https://arxiv.org/abs/2609.15863v1) | 摘要 | native multimodal generation 工作流；摘要未证明 AR 跨窗口历史机制。 | [arXiv 摘要](https://arxiv.org/abs/2609.15863v1) |
| 2026-09-14 | [DIDO: Distilling Interaction-Centric Dynamics into One-Step Denoising for World Action Models](https://arxiv.org/abs/2609.15570v2) | 摘要 | interaction-centric dynamics 蒸馏到 WAM；动作策略范围。 | [arXiv 摘要](https://arxiv.org/abs/2609.15570v2) |
| 2026-09-13 | [World-Action Models for Robot Learning and Control: A Survey](https://arxiv.org/abs/2609.16074v1) | 摘要 | World-Action Models survey；背景文献。 | [arXiv 摘要](https://arxiv.org/abs/2609.16074v1) |
| 2026-09-10 | [Memory as Plans: World-Action Modeling with Memory-Grounded Planning](https://arxiv.org/abs/2609.11561v1) | 摘要 | MaP-WAM：segment language+sparse video 的规划记忆；WAP 执行动作/进度，属于机器人记忆邻接范围。 | [arXiv 摘要](https://arxiv.org/abs/2609.11561v1) |
| 2026-09-08 | [DramaAgent: Agentic Storytelling Video Generation](https://arxiv.org/abs/2610.00097v1) | 正文段落 | story state、角色 stills 和反思属于模型无关的影视 agent 工作流；未确认 AR backbone memory。 | [PDF p.4](https://arxiv.org/pdf/2610.00097v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00097v1#page=5)；§3.2–3.3 |
| 2026-09-08 | [Temporal State Transport in Video Generation: Diagnosing and Correcting Spectral Imbalance](https://arxiv.org/abs/2609.08505v1) | 正文段落 | 频谱平衡与当前视频内 temporal transport；未显示窗口外持久 archive。 | [PDF p.3](https://arxiv.org/pdf/2609.08505v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.08505v1#page=4)；temporal transport / spectral correction |
| 2026-09-06 | [MVWeaver: A Hierarchical Music Video Generation Agent with a Learned Song-to-Visual Bridge](https://arxiv.org/abs/2609.06478v1) | 摘要 | 音乐到视觉的分层 agent；摘要未证明跨镜头历史的具体 carrier。 | [arXiv 摘要](https://arxiv.org/abs/2609.06478v1) |
| 2026-09-06 | [Multi-Grid Post-Training for Long-Form Multi-Shot Video Generation](https://arxiv.org/abs/2609.06373v1) | 正文段落 | noise-free multi-grid context 在同一生成 grid 内联合建模；未证明超出活动 grid 的持续记忆。 | [PDF p.3](https://arxiv.org/pdf/2609.06373v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.06373v1#page=4)；multi-grid context construction |
| 2026-09-04 | [TourPhysics: Bringing Physics to World Models for Exploration and Manipulation from a Single Image](https://arxiv.org/abs/2609.04911v2) | 正文段落 | 确有后续窗口读 committed attention pages 的生成记忆；但未明确确认所用 finite-window diffusion renderer 的 AR 模型/跨 chunk 因果实现。为保证范围，暂缓方法收录；不否认其记忆机制。 | [PDF p.11](https://arxiv.org/pdf/2609.04911v2#page=11), [PDF p.12](https://arxiv.org/pdf/2609.04911v2#page=12)；§4.5 Eqs. (13), (17)–(18) |
| 2026-09-03 | [Puffin-World: Scaling a Unified Multimodal Model with Native 3D World States](https://arxiv.org/abs/2609.04196v1) | 正文段落 | native 3D/多视图状态在联合生成中的表示，未确立跨窗口的生成历史反馈，候选相关几何方法。 | [PDF p.4](https://arxiv.org/pdf/2609.04196v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.04196v1#page=5)；native 3D / joint multiview generation |
| 2026-09-03 | [DSAQuant: Denoising-Stage-Aligned Quantization-Aware Training for Video Generation](https://arxiv.org/abs/2609.04031v1) | 摘要 | denoising-stage quantization-aware training；不是历史内容记忆。 | [arXiv 摘要](https://arxiv.org/abs/2609.04031v1) |
| 2026-09-03 | [Building Pretraining Data for World Models: An Unreal Engine-Based Pipeline for Action-Conditioned Video Generation](https://arxiv.org/abs/2609.03557v1) | 摘要 | Unreal Engine 数据流水线；不是推理期记忆机制。 | [arXiv 摘要](https://arxiv.org/abs/2609.03557v1) |
| 2026-09-03 | [LeanGRPO: Eliminating Redundant Recomputation in Diffusion RL](https://arxiv.org/abs/2609.03528v1) | 摘要 | Diffusion RL 去除重复计算；memory 主要指训练/算力资源。 | [arXiv 摘要](https://arxiv.org/abs/2609.03528v1) |
| 2026-09-02 | [SolarWM: Open Data and Scalable Training for Long-Horizon Video World Models](https://arxiv.org/abs/2609.02886v1) | 正文段落 | 开放数据与可扩展长时训练；通用 baseline，不作为独立新 carrier。 | [PDF p.4](https://arxiv.org/pdf/2609.02886v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.02886v1#page=5)；data/training and generation architecture |
| 2026-09-02 | [SimpleMemVLA: A Simple but Effective Native-Video Memory for Vision-Language-Action Models](https://arxiv.org/abs/2609.05533v2) | 摘要 | SimpleMemVLA：native video history 服务动作 head；属于 VLA 记忆邻接范围。 | [arXiv 摘要](https://arxiv.org/abs/2609.05533v2) |
| 2026-09-01 | [Mind the Rift: Cross-Scale Coupling Mismatch for AI-Generated Video Detection](https://arxiv.org/abs/2609.00742v1) | 摘要 | AI 生成视频检测；不属于生成记忆。 | [arXiv 摘要](https://arxiv.org/abs/2609.00742v1) |
| 2026-09-01 | [Streaming4D: Accelerate 4D World Models via Block-wise Video Generation and Incremental Reconstruction](https://arxiv.org/abs/2609.00610v2) | 正文段落 | 持久 World Memory 用于 4D 重建；正文把几何反馈到 generator 列为 future work，当前路径不能作为生成记忆收录。 | [PDF p.3](https://arxiv.org/pdf/2609.00610v2#page=3)；§3.3; geometry feedback is future work |

## 旧论文近期修订：单独登记

另按 lastUpdatedDate 检索 `video AND memory`，找到 54 篇在窗口内更新但首次提交早于 9 月的论文。下面是与生成记忆或边界诊断较相关的记录。**这里仅核对版本元数据，未逐版本比较方法/实验差异；不计入本次新增数。**

| 论文 | 首次提交 | 当前版本更新 | 仓库状态 / 后续核对 | 来源 |
|---|---|---|---|---|
| WorldCraft: From Camera Navigation to Object Manipulation in Interactive Video World Models | 2026-05-24 | 2026-10-08 (`2605.25077v2`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2605.25077v2) |
| FocusGraph: Graph-Structured Frame Selection for Embodied Long Video Question Answering | 2026-03-04 | 2026-10-01 (`2603.04349v2`) | video QA / 理解方向，不纳入生成方法 | [arXiv](https://arxiv.org/abs/2603.04349v2) |
| EvoState: Closed-Loop Visual State Management for Long-Form Video Generation | 2026-06-15 | 2026-09-30 (`2606.16184v2`) | 仓库已有；本次不重复新增；arXiv 新题名为 EvoState，README 仍为旧题名，先登记待元数据更新 | [arXiv](https://arxiv.org/abs/2606.16184v2) |
| Matrix-Game 3.0: Real-Time and Streaming Interactive World Model with Long-Horizon Memory | 2026-04-10 | 2026-09-29 (`2604.08995v3`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2604.08995v3) |
| Teaching Video Generators to Remember: Eliciting Dynamic Memory for Out-of-Sight State Evolution | 2026-05-25 | 2026-09-29 (`2605.25333v3`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2605.25333v3) |
| EverAnimate: Minute-Scale Human Animation via Latent Flow Restoration | 2026-05-14 | 2026-09-28 (`2605.15042v2`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2605.15042v2) |
| Can Video World Models Track Unobserved World States? | 2026-08-31 | 2026-09-28 (`2608.30692v2`) | 窗口外首发；需要单独追溯正文后决定 | [arXiv](https://arxiv.org/abs/2608.30692v2) |
| 4DStreamCtrl: Interactive Video Generation with Online 4D Control | 2026-08-26 | 2026-09-15 (`2608.25479v3`) | 窗口外首发；需要单独追溯正文后决定 | [arXiv](https://arxiv.org/abs/2608.25479v3) |
| Visko Orbis 1.0: A Live Model for Real-Time Interactive Long Video Generation | 2026-07-29 | 2026-09-08 (`2607.26694v3`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2607.26694v3) |
| AnchorWeave: World-Consistent Video Generation with Retrieved Local Spatial Memories | 2026-02-16 | 2026-09-04 (`2602.14941v2`) | 仓库已有；本次不重复新增 | [arXiv](https://arxiv.org/abs/2602.14941v2) |

## 检索出处与可复核文件

arXiv 查询均以作者提交的原始 metadata / PDF 为核对依据，Web 搜索与项目页用于发现和补查，不以二手论文目录决定分类。分页查询与数量记录在 [search-log.json](2026-10-10-search-log.json)；完整发现元数据在 [discovery.csv](2026-10-10-discovery.csv)，它们尚未逐篇核对。

- [117 篇候选逐项 checklist](2026-10-10-paper-checklist.csv)：日期、版本、状态、核对级别、分类、依据和链接。
- [逐篇结构化记录](2026-10-10-paper-records.json)：另含五视角说明、benchmark 的历史必要性及已下载 PDF 的 SHA-256。
- [旧论文修订元数据](2026-10-10-revisions.json)：54 篇修订快照；metadata-only。
- [arXiv 页面访问与题名核对](2026-10-10-arxiv-page-check.json)：117 项均访问成功，页面题名与发现元数据一致。

本次以 arXiv 和作者项目为主要检索入口，不声称覆盖全部非 arXiv 会议论文，也未复现方法。摘要级待核候选可继续正文复查，已有 revision 需要单独版本差异核对。
