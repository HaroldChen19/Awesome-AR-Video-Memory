# 34 篇近期论文：逐篇 scope、载体与分类再核对

核对日期：**2026-10-11**。对象为本次 PR 保留的 **34 篇独立新论文**；发现时间窗仍为 **2026-09-01 至 2026-10-10**。本轮重新阅读每篇所列版本的相关方法/协议段落，并再次访问 34 个 arXiv 作者提交页面：题名均匹配，页面可见版本均与所核对 PDF 一致。

## 最终清单与分类规则

最终为 **29 篇 memory 方法、2 篇 memory learning、1 篇 AR memory diagnostics、2 篇仅 benchmark**。MosaiChunk / DeCoPrune 的 benchmark 与方法共享论文，因此 README 有 4 个 benchmark 条目、仍是 34 篇独立论文。

| Forms 主载体 | 新增方法 | 子类 |
|---|---:|---|
| Visual Memory | 9 | Pixel 1；VAE 6；宿主相关编码的观测管理 2 |
| Implicit State Memory | 18 | Attention-cache 15；Recurrent 2；Encoded History 1 |
| Explicit State Memory | 2 | Spatial / Geometric 2 |
| Adaptive Parametric Memory | 0 | 本轮无通过 scope 的新增条目 |

分类分两步：先确定论文在 survey 中的**贡献角色**，再记录运行时的**持久历史载体**。仅研究原生 KV writer 的离线学习归 Learning；benchmark / 因果诊断归 Evaluation。Forms 方法按后续生成实际读取的存储对象分类，混合方法同时记副载体。

Visual 保留观测对应关系；Encoded History 是跨观测混合的专用 embedding；Recurrent 是模型递归状态；Attention-cache 是原生历史 K/V；Explicit 保存坐标/实体结构。离线训练的 manager、compressor 或 writer 与 episode 参数记忆分开。Keepsake / SMI 的管理分组仍归 Visual，pixel/latent 编码依宿主，不新增第五类或载体子类。

## 本轮修正

- **SGF+ → Learning**：与 Connected Self Forcing 一致，贡献在离线 context-writer 梯度/参数分工；运行时载体仍记录 KV。
- **WiW → training-free**：§4.1 明确冻结 LingBot-World 2.0 causal-fast；删去此前“动作条件生成训练”的描述。
- **HLA-WM / LOCI**：补记 softmax KV 副载体；固定递归状态/单摘要大小与整体历史 archive 容量分开。
- **Memorizon**：kK 是训练 scored-chunk union bank 的上界；推理单次 top-K 与整个历史池容量分别记录。
- **ZYT-World**：来源明确为跨轨迹 memory logs，AR student 读取该 bank；生成 chunk 的在线写回尚未由所核对段落建立。
- **Artemis / Weave Forcing / ID-Forcing / Custom Forcing / Recency / StateAgent**：修正方法节号；**SAF / AlayaVista / QuantWM / DeCoPrune**：补齐实际 inference / 历史锚点 / 校正 / benchmark 页码。
- **TRAC / Uncertainty DMD**：分别限定 SSC 首段 KV、stochastic cache writing 的 memory 组件。QuantWM 主评测记为 93 frames，避免与分钟级记忆评测混同。

## 逐篇总表

| 论文 / 固定版本 | 最终收录角色 | 持久载体 | 本轮结论 | 主要方法 / 协议出处 |
|---|---|---|---|---|
| [WorldCast](https://arxiv.org/abs/2610.12412v1) `2610.12412v1` | Forms / VAE-space Visual Memory | VAE-space Visual Memory；辅助 Entity-centric States / scene pose-depth metadata | 保留 Visual 主分类与 Explicit 副分类，细化副载体。 | [PDF p.4](https://arxiv.org/pdf/2610.12412v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12412v1#page=5)；§3.2–3.3; Eq. (1) |
| [Connected Self Forcing](https://arxiv.org/abs/2610.12156v1) `2610.12156v1` | Learning / KV writer | 原生 Attention-cache States（运行时）；收录角色 Learning | 保留 Learning，并显式记录运行时 KV 载体。 | [PDF p.4](https://arxiv.org/pdf/2610.12156v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12156v1#page=5)；§3.1–3.3; Figure 3; Eq. (1) |
| [Memory Forcing](https://arxiv.org/abs/2610.11756v1) `2610.11756v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；补充 rolling / DMD 训练背景与固定总预算的三 bank 边界。 | [PDF p.3](https://arxiv.org/pdf/2610.11756v1#page=3), [PDF p.5](https://arxiv.org/pdf/2610.11756v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.11756v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.11756v1#page=7)；§3.1; §3.3–3.4; Algorithm 1; causal student setup |
| [SGF+](https://arxiv.org/abs/2610.10429v2) `2610.10429v2` | Learning / KV writer | 原生 Attention-cache States（运行时）；收录角色 Learning | 从 Forms / Attention-cache 方法列表移到 History-dependent Training；仍在 scope。 | [PDF p.4](https://arxiv.org/pdf/2610.10429v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.10429v2#page=5), [PDF p.6](https://arxiv.org/pdf/2610.10429v2#page=6)；§3.1–3.3; Eqs. (1), (2), (5) |
| [SPW-Nav](https://arxiv.org/abs/2610.08941v1) `2610.08941v1` | Forms / VAE-space Visual Memory | VAE-space Visual Memory | 保留 VAE；确认多尺度 memory 是跨 chunk 唯一连续性接口。 | [PDF p.5](https://arxiv.org/pdf/2610.08941v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.08941v1#page=6)；§4.4; multi-term memory |
| [Keepsake](https://arxiv.org/abs/2610.06588v1) `2610.06588v1` | Forms / Carrier-agnostic Visual Memory Management | Visual Memory（pixel/latent encoding 依宿主） | 保留 generic Visual；明确 README 的管理分组不是第五种 Forms 或新的载体子类。 | [PDF p.4](https://arxiv.org/pdf/2610.06588v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.06588v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.06588v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.06588v1#page=7)；§3.1–3.3; Eqs. (1), (2); Algorithm 1; §4.1 |
| [HLA-WM](https://arxiv.org/abs/2610.05739v1) `2610.05739v1` | Forms / Recurrent and State-space States | Recurrent and State-space States；辅助 Attention-cache States | 补记 Cache 副载体；确认冻结 SANA-WM、training-free。 | [PDF p.5](https://arxiv.org/pdf/2610.05739v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.05739v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.05739v1#page=7)；§4.1–4.4; affine summaries and state recomposition |
| [Artemis](https://arxiv.org/abs/2610.07031v1) `2610.07031v1` | Forms / Spatial and Geometric States | Spatial and Geometric States；辅助 Attention-cache States / agent pose records | 保留 Spatial 主分类；方法出处由 §3.1–3.2 修正为 §4.1–4.3。 | [PDF p.5](https://arxiv.org/pdf/2610.07031v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.07031v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.07031v1#page=7)；§4.1–4.3; Eq. (1); progressive memory update |
| [Weave Forcing](https://arxiv.org/abs/2610.03510v1) `2610.03510v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；方法定位由 §3.2–3.3 修正为 §4.1–4.2。 | [PDF p.3](https://arxiv.org/pdf/2610.03510v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03510v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03510v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.03510v1#page=6)；§3.1; §4.1–4.2; Eq. (5) |
| [In-Distribution Forcing](https://arxiv.org/abs/2610.03120v2) `2610.03120v2` | Forms / Attention-cache States | Attention-cache States | 保留 Cache 和 training-free；§4 定位修正为 §3.1–3.2。 | [PDF p.3](https://arxiv.org/pdf/2610.03120v2#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03120v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03120v2#page=5)；§3.1–3.2; Eq. (4); Algorithm 1 |
| [Custom Forcing](https://arxiv.org/abs/2610.02914v2) `2610.02914v2` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；定位修正为 §3.1–3.2。 | [PDF p.4](https://arxiv.org/pdf/2610.02914v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02914v2#page=5)；§3.1–3.2; Figure 3; persistent reference KV |
| [TRAC](https://arxiv.org/abs/2610.02779v1) `2610.02779v1` | Forms / Attention-cache States | Attention-cache States（SSC component） | 保留 Cache，但将 memory 收录依据限定为 SSC 首段 KV。 | [PDF p.3](https://arxiv.org/pdf/2610.02779v1#page=3), [PDF p.6](https://arxiv.org/pdf/2610.02779v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02779v1#page=7)；§3.1; §3.2.3 Eq. (13); §4.1 |
| [Spatial Memory Intelligence (SMI)](https://arxiv.org/abs/2610.02521v1) `2610.02521v1` | Forms / Carrier-agnostic Visual Memory Management | Visual Memory（pixel/latent encoding 依宿主） | 保留 generic Visual；明确宿主相关编码和管理分组的地位。 | [PDF p.5](https://arxiv.org/pdf/2610.02521v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02521v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02521v1#page=7)；§3.1–3.4; Eqs. (1)–(11) |
| [World Observer](https://arxiv.org/abs/2610.02162v1) `2610.02162v1` | Forms / VAE-space Visual Memory | VAE-space Visual Memory | 保留 VAE；细化固定 sink 与近期 tail 的区别。 | [PDF p.4](https://arxiv.org/pdf/2610.02162v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02162v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02162v1#page=6)；§3; §3.2; observer sink |
| [MosaiChunk](https://arxiv.org/abs/2610.02153v1) `2610.02153v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；RememBench 同论文另记 benchmark，不重复论文计数。 | [PDF p.4](https://arxiv.org/pdf/2610.02153v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02153v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)；§3.1–3.2; §4 RememBench; §5 |
| [Memorizon](https://arxiv.org/abs/2610.00544v1) `2610.00544v1` | Forms / VAE-space Visual Memory | VAE-space Visual Memory | 修正“联合 bank 有 kK 上界”的适用阶段：训练 union，不是整个推理 archive。 | [PDF p.3](https://arxiv.org/pdf/2610.00544v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.00544v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00544v1#page=5)；§3.1–3.4; bounded union bank; causal sliding window |
| [LOCI](https://arxiv.org/abs/2609.40222v1) `2609.40222v1` | Forms / Recurrent and State-space States | Recurrent and State-space States；辅助 Attention-cache States | 保留 Recurrent 主类并补记 Cache 副类；明确 clean commit。 | [PDF p.4](https://arxiv.org/pdf/2609.40222v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.40222v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.40222v1#page=6)；§4.1–4.2; hybrid KDA/softmax; clean-state commit |
| [DeCoPrune](https://arxiv.org/abs/2609.39096v2) `2609.39096v2` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；CMBench 协议起始页修正为 PDF p.4，续页 p.5–6。 | [PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.39096v2#page=6)；§3.1 Eqs. (1), (2); §3.2 CMBench |
| [FrameMorrow](https://arxiv.org/abs/2609.38839v1) `2609.38839v1` | Forms / Pixel-space Visual Memory | Pixel-space Visual Memory | 保留 Pixel；确认 prospective tokens 是当步查询，非持久 recurrent memory。 | [PDF p.4](https://arxiv.org/pdf/2609.38839v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38839v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38839v1#page=6)；§3; Eq. (9); §4.1 AR hosts |
| [Self-Aligned Forcing (SAF)](https://arxiv.org/abs/2609.38114v1) `2609.38114v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；增加 p.6 inference bank 的直接出处。 | [PDF p.4](https://arxiv.org/pdf/2609.38114v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38114v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38114v1#page=6)；§3.1–3.2; §3.4–3.5; Eq. (6) |
| [Honeycomb](https://arxiv.org/abs/2609.37690v2) `2609.37690v2` | Forms / Spatial and Geometric States | Spatial and Geometric States | 保留 Spatial；细化 constant-size 的对象为 HexMemory feature tensors。 | [PDF p.4](https://arxiv.org/pdf/2609.37690v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37690v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.37690v2#page=6)；§3.1–3.6; HexMemory; overlapping AR chunks |
| [Compress to Remember (PACC)](https://arxiv.org/abs/2609.36364v1) `2609.36364v1` | Forms / Encoded History States | Encoded History States | 保留 Encoded History；确认 query 数并非全时长恒定。 | [PDF p.3](https://arxiv.org/pdf/2609.36364v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.36364v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.36364v1#page=5)；§3.1–3.3; Eq. (1); prediction matching |
| [OPIS](https://arxiv.org/abs/2609.35052v1) `2609.35052v1` | Evaluation / OPIS | Evaluation / Memory-oriented Benchmark（无新增 model carrier） | 保留仅 benchmark；限定 AR camera-driven 模型与历史依赖子集。 | [PDF p.4](https://arxiv.org/pdf/2609.35052v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.35052v1#page=5), [PDF p.8](https://arxiv.org/pdf/2609.35052v1#page=8)；§3.1; §4; §5.1 camera-driven models |
| [Geometry as Address (GEAR)](https://arxiv.org/abs/2609.34722v1) `2609.34722v1` | Forms / VAE-space Visual Memory | VAE-space Visual Memory；辅助 Spatial and Geometric States（visibility） | 保留 VAE + Explicit；精确限定 octree 的语义。 | [PDF p.3](https://arxiv.org/pdf/2609.34722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34722v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34722v1#page=5)；§3.1–3.3; latent bank; Invisible Octree |
| [WorldAttention](https://arxiv.org/abs/2609.34606v1) `2609.34606v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；记录 active budget 与 full archive 分离。 | [PDF p.3](https://arxiv.org/pdf/2609.34606v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34606v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34606v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.34606v1#page=6)；§3.1–3.2; hierarchical cache; HSA; §4 setup |
| [In-Flight KV Cache (FlashForward)](https://arxiv.org/abs/2609.32540v2) `2609.32540v2` | Forms / Attention-cache States | Attention-cache States | 保留 Cache，并持续保留 README 的 two-sided-anchor 条件标注。 | [PDF p.5](https://arxiv.org/pdf/2609.32540v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.32540v2#page=6)；§3.1; Eq. (2); AR planner and renderer |
| [QuantWM](https://arxiv.org/abs/2609.26425v3) `2609.26425v3` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；补 p.6 校正对象及 p.7 AR hosts；删去泛称“长时生成”实验。 | [PDF p.4](https://arxiv.org/pdf/2609.26425v3#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26425v3#page=5), [PDF p.6](https://arxiv.org/pdf/2609.26425v3#page=6), [PDF p.7](https://arxiv.org/pdf/2609.26425v3#page=7)；§4.1–4.2; correction C; §5.1 AR hosts |
| [ZYT-World](https://arxiv.org/abs/2609.21712v2) `2609.21712v2` | Forms / VAE-space Visual Memory | VAE-space Visual Memory | 保留 VAE；把来源修正为 cross-trajectory memory logs，区分 native KV。 | [PDF p.3](https://arxiv.org/pdf/2609.21712v2#page=3), [PDF p.7](https://arxiv.org/pdf/2609.21712v2#page=7), [PDF p.10](https://arxiv.org/pdf/2609.21712v2#page=10), [PDF p.14](https://arxiv.org/pdf/2609.21712v2#page=14), [PDF p.15](https://arxiv.org/pdf/2609.21712v2#page=15)；AR student; Figure 6; §3.6; §4.6 |
| [Recency Forcing](https://arxiv.org/abs/2609.19729v1) `2609.19729v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；方法定位由 §4 修正为 §3.2–3.4；补 training-free 配置。 | [PDF p.4](https://arxiv.org/pdf/2609.19729v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.19729v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.19729v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.19729v1#page=7)；§3.2–3.4; TRB; BAR; setup |
| [AlayaVista](https://arxiv.org/abs/2609.14462v1) `2609.14462v1` | Forms / Attention-cache States | Attention-cache States | 保留 Cache；补 p.9–10 beyond-local early-anchor 的依据。 | [PDF p.7](https://arxiv.org/pdf/2609.14462v1#page=7), [PDF p.9](https://arxiv.org/pdf/2609.14462v1#page=9), [PDF p.10](https://arxiv.org/pdf/2609.14462v1#page=10)；§3.3; §3.6.1 Eq. (11); spectral anchor |
| [Causal Audit of Memory Specificity](https://arxiv.org/abs/2609.12090v1) `2609.12090v1` | Evaluation / Memory Diagnostics | Evaluation / Memory Diagnostics（WorldMem generative arm） | 保留诊断角色，限定 WorldMem 实验。 | [PDF p.5](https://arxiv.org/pdf/2609.12090v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.12090v1#page=7)；§4.2 WorldMem; §5.5 Figure 3 |
| [World in World (WiW)](https://arxiv.org/abs/2609.11548v1) `2609.11548v1` | Forms / Attention-cache States | Attention-cache States | Learning 修正为 training-free；全部 LingBot-World2 causal-fast 参数冻结，无新训练或控制 adapter。 | [PDF p.4](https://arxiv.org/pdf/2609.11548v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11548v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11548v1#page=7)；causal rollout; §3.4; §4.1 |
| [Uncertainty DMD](https://arxiv.org/abs/2609.11265v1) `2609.11265v1` | Forms / Attention-cache States | Attention-cache States（stochastic cache writing） | 保留 Cache；把记忆贡献限定为 component B 的 stochastic cache writing。 | [PDF p.4](https://arxiv.org/pdf/2609.11265v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11265v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11265v1#page=7)；AR formulation; §4.2–4.3; Algorithm 1 line 16 |
| [StateBench](https://arxiv.org/abs/2609.03673v1) `2609.03673v1` | Evaluation / StateBench | Evaluation / StateBench（MAGI-1 AR arm；StateAgent 方法排除） | 短名显示为 StateBench；StateAgent 方法定位修正为 §4.4 Eq. (12)。 | [PDF p.4](https://arxiv.org/pdf/2609.03673v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.03673v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.03673v1#page=7), [PDF p.8](https://arxiv.org/pdf/2609.03673v1#page=8), [PDF p.13](https://arxiv.org/pdf/2609.03673v1#page=13)；§3.1–3.2 StateBench; §4.4 Eq. (12); §5.1; Table 1 |

## 每篇的写入、读取与分类依据

### 01. WorldCast — 2610.12412v1

[WorldCast: Distributed Multiplayer World Models](https://arxiv.org/abs/2610.12412v1)；首次提交 2026-10-08，所核对版本更新 2026-10-08。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory；辅助 Entity-centric States / scene pose-depth metadata。
- **AR 依据**：场景 memory latents 先置，recent/target 在 block-causal mask 下读取。 [PDF p.5](https://arxiv.org/pdf/2610.12412v1#page=5)；§3.3; block-causal generator。
- **保存 / 写入**：共享 scene bank 发布 latent block、相机和粗 depth；逐 block 更新玩家位置、朝向及武器状态，撤回冗余场景项。
- **后续读取**：后续 block-causal generator 读取 scene bank 与玩家状态条件；离屏玩家状态仍保留。
- **分类判断**：历史外观的持久对象是可解码 VAE latent；玩家字段是独立结构化副载体。
- **本轮处理**：保留 Visual 主分类与 Explicit 副分类，细化副载体。
- **解释边界**：相机/depth 元数据与 player state 分开登记；共享 bank 不是已证明的全外观融合 3D 地图。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.12412v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12412v1#page=5)；§3.2–3.3; Eq. (1)。

### 02. Connected Self Forcing — 2610.12156v1

[Connected Self Forcing: Beyond Local Learning in Video Autoregression](https://arxiv.org/abs/2610.12156v1)；首次提交 2026-10-08，所核对版本更新 2026-10-08。

- **收录角色**：Learning / KV writer。**载体**：原生 Attention-cache States（运行时）；收录角色 Learning。
- **AR 依据**：AR chunk generator 及 retained KV writer 被明确分开；shortcut replay 训练跨历史缓存的梯度路径。 [PDF p.4](https://arxiv.org/pdf/2610.12156v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12156v1#page=5)；§3.1–3.3; KV writer and replay。
- **保存 / 写入**：离线 shortcut replay 恢复已生成 latent 与 KV writer 的梯度；运行时沿用生成后写入历史 KV 的接口。
- **后续读取**：后续 AR chunk 从保留 KV 读取；未来损失训练 writer，未来视频不作为推理输入。
- **分类判断**：贡献是历史写入路径的学习，而非新增持久载体或逐 episode 参数适应。
- **本轮处理**：保留 Learning，并显式记录运行时 KV 载体。
- **解释边界**：训练梯度穿越历史与推理时可读取未来是两种不同信息路径。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.12156v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.12156v1#page=5)；§3.1–3.3; Figure 3; Eq. (1)。

### 03. Memory Forcing — 2610.11756v1

[Memory Forcing: Attendable Mid-Horizon History for Streaming Video Generation](https://arxiv.org/abs/2610.11756v1)；首次提交 2026-10-08，所核对版本更新 2026-10-08。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：逐块因果生成；三 bank K/V 被后续 denoising 读取。 [PDF p.3](https://arxiv.org/pdf/2610.11756v1#page=3), [PDF p.5](https://arxiv.org/pdf/2610.11756v1#page=5), [PDF p.7](https://arxiv.org/pdf/2610.11756v1#page=7)；AR formulation; Algorithm 1; causal student。
- **保存 / 写入**：clean chunk 写入 working；working 满时把与新块最不相似的块移入 archive，archive 满则 FIFO 淘汰；sink 固定。
- **后续读取**：当前查询拼接 sink / archive / working / current 的 KV，读取前重新分配 bank-aware RoPE。
- **分类判断**：被保留和重读的是模型原生历史 KV；中期 archive 直接改变窗口外内容可访问性。
- **本轮处理**：保留 Cache；补充 rolling / DMD 训练背景与固定总预算的三 bank 边界。
- **解释边界**：2610.11756 与仓库既有 2510.03198 同名 Memory Forcing 是不同论文。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2610.11756v1#page=3), [PDF p.5](https://arxiv.org/pdf/2610.11756v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.11756v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.11756v1#page=7)；§3.1; §3.3–3.4; Algorithm 1; causal student setup。

### 04. SGF+ — 2610.10429v2

[SGF+: Decoupling Gradient Flows for Autoregressive Video Generation](https://arxiv.org/abs/2610.10429v2)；首次提交 2026-10-07，所核对版本更新 2026-10-08。

- **收录角色**：Learning / KV writer。**载体**：原生 Attention-cache States（运行时）；收录角色 Learning。
- **AR 依据**：latent blocks 按序生成，context writer 写历史，denoiser 读 context K/V。 [PDF p.4](https://arxiv.org/pdf/2610.10429v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.10429v2#page=5)；§3.1–3.3; Eq. (1)。
- **保存 / 写入**：离线重构 context KV 的可微路径，context writer 与 denoiser 分离参数/梯度；生成历史由 writer 编码为 KV。
- **后续读取**：AR denoiser 从 context KV 读取，writer 由未来生成目标监督。
- **分类判断**：与 CSF 一致按贡献角色归 Learning；运行时历史仍是 KV，离线分离参数不构成 Adaptive Parametric Memory。
- **本轮处理**：从 Forms / Attention-cache 方法列表移到 History-dependent Training；仍在 scope。
- **解释边界**：writer 与 denoiser 的离线参数优化不等于将本次轨迹在线写进权重。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.10429v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.10429v2#page=5), [PDF p.6](https://arxiv.org/pdf/2610.10429v2#page=6)；§3.1–3.3; Eqs. (1), (2), (5)。

### 05. SPW-Nav — 2610.08941v1

[SPW-Nav: A Streaming Panoramic World Model for Language-Guided Navigation](https://arxiv.org/abs/2610.08941v1)；首次提交 2026-10-06，所核对版本更新 2026-10-06。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory。
- **AR 依据**：基于 Helios 的 AR recipe；历史 latent tokens 条件化非重叠下一 chunk。 [PDF p.5](https://arxiv.org/pdf/2610.08941v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.08941v1#page=6)；§4.4; streaming generator。
- **保存 / 写入**：生成后的 panorama latent 按近期、较早历史及固定首帧 anchor 分档保留；旧项采用更粗 patchify。
- **后续读取**：Helios AR recipe 的下一非重叠 chunk 读取多尺度历史 token；相机旋转在初始全景朝向与解码输出之间处理。
- **分类判断**：历史项保持 observation-aligned latent；相对 pose 是条件/地址，不是持久度量地图。
- **本轮处理**：保留 VAE；确认多尺度 memory 是跨 chunk 唯一连续性接口。
- **解释边界**：全景旋转覆盖与远距离平移重访的证据分别解释。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2610.08941v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.08941v1#page=6)；§4.4; multi-term memory。

### 06. Keepsake — 2610.06588v1

[Keepsake: Selective Spatial Memory for Long-Horizon Video Generation](https://arxiv.org/abs/2610.06588v1)；首次提交 2026-10-05，所核对版本更新 2026-10-05。

- **收录角色**：Forms / Carrier-agnostic Visual Memory Management。**载体**：Visual Memory（pixel/latent encoding 依宿主）。
- **AR 依据**：Eq. (1) 显式按 previous chunk 与检索历史生成 next chunk；实际宿主为 MemCam / WorldMem。 [PDF p.4](https://arxiv.org/pdf/2610.06588v1#page=4), [PDF p.6](https://arxiv.org/pdf/2610.06588v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.06588v1#page=7)；§3.1 Eqs. (1)–(2); §4.1 hosts。
- **保存 / 写入**：合并旧观测 bank 与新 chunk；用 pose / appearance 冗余关系迭代淘汰，保留固定预算观测。
- **后续读取**：next-chunk 公式读上一 chunk 与从 bank 检索的观测；MemCam / WorldMem 是实际生成宿主。
- **分类判断**：持久 payload 是观测，关系图是保留操作中的评分结构；论文没有统一固定两个宿主的像素/latent 编码。
- **本轮处理**：保留 generic Visual；明确 README 的管理分组不是第五种 Forms 或新的载体子类。
- **解释边界**：DINO 或 VAE 用作评分特征，不足以单独证明整个 bank 的存储格式。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.06588v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.06588v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.06588v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.06588v1#page=7)；§3.1–3.3; Eqs. (1), (2); Algorithm 1; §4.1。

### 07. HLA-WM — 2610.05739v1

[HLA-WM: Hybrid Linear Attention for Long-Horizon Video World Models](https://arxiv.org/abs/2610.05739v1)；首次提交 2026-10-05，所核对版本更新 2026-10-05。

- **收录角色**：Forms / Recurrent and State-space States。**载体**：Recurrent and State-space States；辅助 Attention-cache States。
- **AR 依据**：已有 SANA-WM AR generator；历史 chunk summaries 重组为当前查询的 GDN 状态。 [PDF p.1](https://arxiv.org/pdf/2610.05739v1#page=1), [PDF p.5](https://arxiv.org/pdf/2610.05739v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.05739v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.05739v1#page=7)；base SANA-WM; §4.1–4.4。
- **保存 / 写入**：历史 chunk 产生仿射摘要 (A_i, B_i) 并缓存；同时保留可选历史的 softmax KV。
- **后续读取**：按几何检索的 chunks 重组当前查询的 GDN recurrent state，softmax 分支读取同一批历史 KV。
- **分类判断**：线性注意力状态重组是主贡献，softmax KV 是独立混合副载体；相机检索并不把 state 变成几何地图。
- **本轮处理**：补记 Cache 副载体；确认冻结 SANA-WM、training-free。
- **解释边界**：单摘要大小固定，但摘要数量随 chunk 增长；不能把整个历史 archive 描述为恒定总容量。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2610.05739v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.05739v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.05739v1#page=7)；§4.1–4.4; affine summaries and state recomposition。

### 08. Artemis — 2610.07031v1

[Artemis: Geometry-Grounded Multi-Agent Driving World Models with Shared 3D State and Progressive Memory Update](https://arxiv.org/abs/2610.07031v1)；首次提交 2026-10-04，所核对版本更新 2026-10-04。

- **收录角色**：Forms / Spatial and Geometric States。**载体**：Spatial and Geometric States；辅助 Attention-cache States / agent pose records。
- **AR 依据**：多主体的 joint future 按历史逐步生成，并更新共享地图和历史 KV。 [PDF p.5](https://arxiv.org/pdf/2610.07031v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.07031v1#page=6)；§4.1; autoregressive joint factorization。
- **保存 / 写入**：关键帧扩展静态共享 3D map；动态/uncontrolled 观测进 buffer，代理 pose memory 记录主体；各代理另存历史 KV。
- **后续读取**：多主体 AR joint future 读取投影地图、agent proxy/pose 与历史缓存；共享几何跨主体复用。
- **分类判断**：共享坐标地图是主持久对象；每代理 KV 和 pose 记录是混合副载体。
- **本轮处理**：保留 Spatial 主分类；方法出处由 §3.1–3.2 修正为 §4.1–4.3。
- **解释边界**：数据集 §3.2 与方法 §4 的证据分开；动态 buffer 不等于所有动态对象均融合进静态地图。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2610.07031v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.07031v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.07031v1#page=7)；§4.1–4.3; Eq. (1); progressive memory update。

### 09. Weave Forcing — 2610.03510v1

[Weave Forcing: Compositional Memory Routing for Interactive Long Video Generation](https://arxiv.org/abs/2610.03510v1)；首次提交 2026-10-02，所核对版本更新 2026-10-02。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：因果 DiT 的 AR latent blocks；实现为 Self Forcing backbone。 [PDF p.3](https://arxiv.org/pdf/2610.03510v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03510v1#page=4), [PDF p.6](https://arxiv.org/pdf/2610.03510v1#page=6)；§3.1; §4.1。
- **保存 / 写入**：历史镜头 KV 按 query 权重压缩并保留；历史镜头语义用于索引/路由。
- **后续读取**：当前语义 slots 路由历史镜头，grouped attention 读取压缩 KV；使用因果 Self Forcing backbone。
- **分类判断**：语义 slot 是路由输入，实际持续内容在 KV；没有可独立演化的实体状态表。
- **本轮处理**：保留 Cache；方法定位由 §3.2–3.3 修正为 §4.1–4.2。
- **解释边界**：把路由语义与独立 Entity-centric State 分开登记。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2610.03510v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03510v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03510v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.03510v1#page=6)；§3.1; §4.1–4.2; Eq. (5)。

### 10. In-Distribution Forcing — 2610.03120v2

[In-Distribution Forcing for Long Video Generation at Test Time](https://arxiv.org/abs/2610.03120v2)；首次提交 2026-10-02，所核对版本更新 2026-10-07。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：因果 AR 推理沿用生成历史 K/V，改变 self-caching 的写入分布。 [PDF p.3](https://arxiv.org/pdf/2610.03120v2#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03120v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03120v2#page=5)；AR setup; §3.1–3.2 Self-Caching。
- **保存 / 写入**：Self-Caching 对选定历史 clean chunk 重建 in-distribution KV provenance，保留 sink 与按规则缓存的近期条目。
- **后续读取**：next chunk 按 conditioning / caching window 规则读取保留 KV，并调节时间位置。
- **分类判断**：直接改变历史 KV 的写入来源与读取方式；供重缓存的 latent 是输入材料，主记忆接口是 KV。
- **本轮处理**：保留 Cache 和 training-free；§4 定位修正为 §3.1–3.2。
- **解释边界**：稳定外推来自 KV provenance 的控制，不能直接解读为完整远期 archive。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2610.03120v2#page=3), [PDF p.4](https://arxiv.org/pdf/2610.03120v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.03120v2#page=5)；§3.1–3.2; Eq. (4); Algorithm 1。

### 11. Custom Forcing — 2610.02914v2

[Custom Forcing: Training-Free Subject Customization for Autoregressive Video Generation](https://arxiv.org/abs/2610.02914v2)；首次提交 2026-10-02，所核对版本更新 2026-10-05。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：AR backbone 的每个 chunk 读永久 reference/custom anchor K/V。 [PDF p.4](https://arxiv.org/pdf/2610.02914v2#page=4)；§3.1–3.2; Figure 3。
- **保存 / 写入**：主体 reference / custom anchors 一次编码成 KV，作为永久参考缓存保留。
- **后续读取**：冻结 AR backbone 的后续 chunks 持续读取 reference/anchor KV，配合位置控制。
- **分类判断**：持续存储和读取的是参考 KV；customization 来自条件注入。
- **本轮处理**：保留 Cache；定位修正为 §3.1–3.2。
- **解释边界**：FLUX 参考图生成和离线模型参数均不作为 episode 参数记忆。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.02914v2#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02914v2#page=5)；§3.1–3.2; Figure 3; persistent reference KV。

### 12. TRAC — 2610.02779v1

[TRAC: Trajectory-aware Reuse and Adaptive Correction for Efficient Autoregressive Video Generation](https://arxiv.org/abs/2610.02779v1)；首次提交 2026-10-02，所核对版本更新 2026-10-02。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States（SSC component）。
- **AR 依据**：chunk AR formulation；SkyReels-V2 / FramePack-F1 实际宿主；首 chunk K/V 参与后续校正。 [PDF p.3](https://arxiv.org/pdf/2610.02779v1#page=3), [PDF p.6](https://arxiv.org/pdf/2610.02779v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02779v1#page=7)；§3.1; §3.2.3; §4.1。
- **保存 / 写入**：首个 chunk 的 K/V 保留为长期结构锚点。
- **后续读取**：后续 chunk 的结构校正 SSC 查询首段池化 KV；实际 AR 宿主包含 SkyReels-V2 / FramePack-F1。
- **分类判断**：SSC 提供明确跨 chunk 历史读取；RCS / ATGS 的 denoising 计算复用单独作为加速组件。
- **本轮处理**：保留 Cache，但将 memory 收录依据限定为 SSC 首段 KV。
- **解释边界**：不能用同一 chunk 内的计算复用代替生成历史记忆的证据。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2610.02779v1#page=3), [PDF p.6](https://arxiv.org/pdf/2610.02779v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02779v1#page=7)；§3.1; §3.2.3 Eq. (13); §4.1。

### 13. Spatial Memory Intelligence (SMI) — 2610.02521v1

[Spatial Memory Intelligence: Endowing World Models with Understanding-Driven Long-Term Memory](https://arxiv.org/abs/2610.02521v1)；首次提交 2026-10-01，所核对版本更新 2026-10-01。

- **收录角色**：Forms / Carrier-agnostic Visual Memory Management。**载体**：Visual Memory（pixel/latent encoding 依宿主）。
- **AR 依据**：action-conditioned AR video 的序列分解；管理历史 chunk bank，并用于 next chunk。 [PDF p.5](https://arxiv.org/pdf/2610.02521v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02521v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02521v1#page=7)；§3.1 Eq. (1); §3.2–3.4。
- **保存 / 写入**：bank 保存历史 video chunks；按空间簇覆盖、可靠性和预算选择保留观测。
- **后续读取**：action-conditioned AR next chunk 读取近期与动作相关检索项；WorldPlay-1.5 的两个宿主实际运行管理器。
- **分类判断**：持续 payload 是视频观测；空间簇与 SFT manager 是管理操作，不能由此改归几何或参数载体。
- **本轮处理**：保留 generic Visual；明确宿主相关编码和管理分组的地位。
- **解释边界**：论文未给出跨两个宿主统一的 RGB/VAE 存储子类型；Qwen manager 是离线训练。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2610.02521v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02521v1#page=6), [PDF p.7](https://arxiv.org/pdf/2610.02521v1#page=7)；§3.1–3.4; Eqs. (1)–(11)。

### 14. World Observer — 2610.02162v1

[World Observer: Joint Actor-Observer Generation for Persistent World Modeling](https://arxiv.org/abs/2610.02162v1)；首次提交 2026-10-01，所核对版本更新 2026-10-01。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory。
- **AR 依据**：正文明确以 tail latents 为历史，autoregressively in chunks；observer 历史与 sink 保留视野外证据。 [PDF p.4](https://arxiv.org/pdf/2610.02162v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02162v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02162v1#page=6)；§3; §3.2。
- **保存 / 写入**：保留 actor/observer tail latents；初始四个 panorama perspective 的 VAE sink 固定保留。
- **后续读取**：后续联合 actor/observer chunks 读取 tail 与始终附加的 observer sink，提供 actor 视野外内容。
- **分类判断**：观测视角仍是可解码 latent；初始 depth warp 是几何条件而非持续融合地图。
- **本轮处理**：保留 VAE；细化固定 sink 与近期 tail 的区别。
- **解释边界**：把不可见区域的视觉条件与显式持久 3D 世界状态分开。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.02162v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02162v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02162v1#page=6)；§3; §3.2; observer sink。

### 15. MosaiChunk — 2610.02153v1

[MosaiChunk: Compositing Spatio-Temporal Memory for Autoregressive Video Generation](https://arxiv.org/abs/2610.02153v1)；首次提交 2026-10-01，所核对版本更新 2026-10-01。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：AR 流式生成的 current context 与历史 K/V sections 拼接，测试淘汰后的重现。 [PDF p.4](https://arxiv.org/pdf/2610.02153v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02153v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)；§3.1–3.2; §4。
- **保存 / 写入**：历史 KV 原样分区存入 CPU，router descriptors 用于检索；保留超出 active window 的 section。
- **后续读取**：top-N sections 的 K/V 拼接进入当前 attention，并缩放 value 权重。
- **分类判断**：mosaic 的持续内容是 KV sections，descriptor 不是替代性的历史载体。
- **本轮处理**：保留 Cache；RememBench 同论文另记 benchmark，不重复论文计数。
- **解释边界**：冻结 backbone 的 router self-distillation 是离线学习。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2610.02153v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.02153v1#page=5), [PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)；§3.1–3.2; §4 RememBench; §5。

- **同论文 benchmark**：RememBench；离开 active window 后的 T2V 重现与 I2V 相机重访；测试历史内容恢复。 [§4; PDF p.6](https://arxiv.org/pdf/2610.02153v1#page=6)。

### 16. Memorizon — 2610.00544v1

[Memorizon: Training World Models Beyond Their Context Window](https://arxiv.org/abs/2610.00544v1)；首次提交 2026-09-30，所核对版本更新 2026-09-30。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory。
- **AR 依据**：chunk 内双向、chunk 间因果；后续 scored chunks 检索历史 latent union bank。 [PDF p.4](https://arxiv.org/pdf/2610.00544v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00544v1#page=5)；§3.2 Causal Sliding Window; §3.3。
- **保存 / 写入**：完成的观测 latent 与相机位姿可供历史池检索；训练把 k 个 scored chunks 的 top-K 结果打包为 union bank。
- **后续读取**：下一 causal chunk 按共视性检索 top-K 历史 latent；训练 union bank 复用检索结果。
- **分类判断**：视觉内容保持观测对齐；几何是检索地址。kK 容量上界属于训练打包的 union。
- **本轮处理**：修正“联合 bank 有 kK 上界”的适用阶段：训练 union，不是整个推理 archive。
- **解释边界**：单次查询 top-K 有界；整个推理历史池的恒定总容量未由该训练上界建立。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2610.00544v1#page=3), [PDF p.4](https://arxiv.org/pdf/2610.00544v1#page=4), [PDF p.5](https://arxiv.org/pdf/2610.00544v1#page=5)；§3.1–3.4; bounded union bank; causal sliding window。

### 17. LOCI — 2609.40222v1

[LOCI: Spatial Linear Memory for Streaming World Models](https://arxiv.org/abs/2609.40222v1)；首次提交 2026-09-30，所核对版本更新 2026-09-30。

- **收录角色**：Forms / Recurrent and State-space States。**载体**：Recurrent and State-space States；辅助 Attention-cache States。
- **AR 依据**：Wan 改为 chunk-causal；当前查询读前 chunk 的 KDA state，最终 clean chunk 写入提交状态。 [PDF p.4](https://arxiv.org/pdf/2609.40222v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.40222v1#page=5)；§4; chunk-causal architecture and committed state。
- **保存 / 写入**：最终 clean chunk 的独立 pass 提交 KDA state；hybrid / historical softmax 层及 camera KV 保留历史。
- **后续读取**：当前 denoising 读取已提交的 S_(c-1)，不在每个去噪步骤修改它；softmax 分支读取自己的历史缓存。
- **分类判断**：递归状态是主载体，softmax KV 是真实混合副载体；camera positional encoding 本身没有可更新几何地图。
- **本轮处理**：保留 Recurrent 主类并补记 Cache 副类；明确 clean commit。
- **解释边界**：递归 state 的固定大小不能作为所有 softmax/camera 历史缓存的总存储上界。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.40222v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.40222v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.40222v1#page=6)；§4.1–4.2; hybrid KDA/softmax; clean-state commit。

### 18. DeCoPrune — 2609.39096v2

[DeCoPrune: Efficient KV-Cache Pruning for Autoregressive Video Diffusion via Denoising Consistency](https://arxiv.org/abs/2609.39096v2)；首次提交 2026-09-30，所核对版本更新 2026-10-05。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：AR 历史 K/V 经共享 token mask 裁剪，后续生成读取保留缓存。 [PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.39096v2#page=6)；§3.1–3.2; cached attention。
- **保存 / 写入**：用 probe 与 final x0 的去噪差异选择 token；块离开近期窗口后，按共享 mask 将各层 KV 压缩入长期 cache。
- **后续读取**：未来 attention 读取长期 pruned KV、保护的 sink 与近期 dense KV。
- **分类判断**：x0 用于计算选取分数，真正持久内容是筛选后的 KV。
- **本轮处理**：保留 Cache；CMBench 协议起始页修正为 PDF p.4，续页 p.5–6。
- **解释边界**：benchmark 数据制作所用生成模型与评测中的 AR continuation 模型分别核对。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.39096v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.39096v2#page=6)；§3.1 Eqs. (1), (2); §3.2 CMBench。

- **同论文 benchmark**：CMBench；58 episodes / 116 tasks；Reappear 与 Revisit 对已见内容提出历史依赖。 [§3.2 (continues pp.5–6); PDF p.4](https://arxiv.org/pdf/2609.39096v2#page=4)。

### 19. FrameMorrow — 2609.38839v1

[FrameMorrow: Future-guided Frame Selection with Prospective Tokens for Long-Horizon Video Generation](https://arxiv.org/abs/2609.38839v1)；首次提交 2026-09-30，所核对版本更新 2026-09-30。

- **收录角色**：Forms / Pixel-space Visual Memory。**载体**：Pixel-space Visual Memory。
- **AR 依据**：实际 AR 宿主包括 Self Forcing、Causal Forcing、CausVid、LongLive；选中历史帧经原生接口条件化未来。 [PDF p.4](https://arxiv.org/pdf/2609.38839v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38839v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38839v1#page=6)；§3 Eq. (9); §4.1 AR hosts。
- **保存 / 写入**：外部 bank 保留历史 RGB frames；每步重算 prospective tokens 并选择需要回收的历史帧。
- **后续读取**：选中 RGB 经 Γ_b 原生条件适配器编码注入 AR generator；实际宿主包括 Self/Causal Forcing、CausVid、LongLive。
- **分类判断**：以适配器之前的持续对象判定为 Pixel；临时 query tokens 与读取时的 latent/KV 不替代 bank 载体。
- **本轮处理**：保留 Pixel；确认 prospective tokens 是当步查询，非持久 recurrent memory。
- **解释边界**：realized future 只用于离线学习；推理选择基于过去与可用条件。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.38839v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38839v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38839v1#page=6)；§3; Eq. (9); §4.1 AR hosts。

### 20. Self-Aligned Forcing (SAF) — 2609.38114v1

[Self-Aligned Forcing: Streaming Video Diffusion with Differentiable Noisy History](https://arxiv.org/abs/2609.38114v1)；首次提交 2026-09-29，所核对版本更新 2026-09-29。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：流式 AR chunks 读取 stage-aligned noisy-history K/V 与 clean sink。 [PDF p.4](https://arxiv.org/pdf/2609.38114v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38114v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38114v1#page=6)；§3.1–3.2; §3.4–3.5 inference bank。
- **保存 / 写入**：按 denoising stage 写 history KV，永久保留 shared clean sink；inference 使用 MultiBank 或 SingleBankMix。
- **后续读取**：后续 AR chunks 从对应 stage 的 noisy-history KV 与 clean sink 读取条件。
- **分类判断**：历史 KV 跨 chunk 保留，直接改变 writer/reader 的噪声阶段配对。
- **本轮处理**：保留 Cache；增加 p.6 inference bank 的直接出处。
- **解释边界**：stage-aligned 跨块历史与当块去噪中间值复用分开。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.38114v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.38114v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.38114v1#page=6)；§3.1–3.2; §3.4–3.5; Eq. (6)。

### 21. Honeycomb — 2609.37690v2

[Honeycomb: Constant-Size Scene Memory Representation for Video World Models](https://arxiv.org/abs/2609.37690v2)；首次提交 2026-09-29，所核对版本更新 2026-09-30。

- **收录角色**：Forms / Spatial and Geometric States。**载体**：Spatial and Geometric States。
- **AR 依据**：§3.6 明确 autoregressively in overlapping chunks；边界 latent 及 HexMemory readout 条件化下一 chunk。 [PDF p.4](https://arxiv.org/pdf/2609.37690v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37690v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.37690v2#page=6)；§3.1–3.6; overlapping AR chunks。
- **保存 / 写入**：完成的 AR chunk 按空间/时空坐标投影并更新六个 HexMemory feature planes。
- **后续读取**：后续重叠 AR chunk 从坐标平面 readout，配合边界 latent、warp/fusion 与 confidence。
- **分类判断**：可按空间地址寻址的六平面是持久载体；learned recurrent update 不改变坐标结构的几何性质。
- **本轮处理**：保留 Spatial；细化 constant-size 的对象为 HexMemory feature tensors。
- **解释边界**：固定特征张量容量不自动约束所有辅助坐标/深度元数据；范围扩展会降低平面空间分辨率。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.37690v2#page=4), [PDF p.5](https://arxiv.org/pdf/2609.37690v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.37690v2#page=6)；§3.1–3.6; HexMemory; overlapping AR chunks。

### 22. Compress to Remember (PACC) — 2609.36364v1

[Compress to Remember: Learning Compact Memory via On-Policy Distillation for Long Video Generation](https://arxiv.org/abs/2609.36364v1)；首次提交 2026-09-28，所核对版本更新 2026-09-28。

- **收录角色**：Forms / Encoded History States。**载体**：Encoded History States。
- **AR 依据**：正文指定 AR generator；周期压缩已完成 prefix，未来 chunk 检索并读取 memory embeddings。 [PDF p.3](https://arxiv.org/pdf/2609.36364v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.36364v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.36364v1#page=5)；§3.1; frozen Wan-based AR generator。
- **保存 / 写入**：learned query embeddings 跨源帧 attention 压缩已完成 prefix 为 M；query 数随 prefix/压缩配置设置。
- **后续读取**：冻结 Wan AR generator 的后续 chunk 读取压缩 M，连续生成另有原生 KV。
- **分类判断**：M 跨帧混合且没有逐观测的 VAE 对应关系；它是独立压缩历史 embedding。
- **本轮处理**：保留 Encoded History；确认 query 数并非全时长恒定。
- **解释边界**：压缩历史 pool 与当前活跃 token 预算分开登记。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2609.36364v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.36364v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.36364v1#page=5)；§3.1–3.3; Eq. (1); prediction matching。

### 23. OPIS — 2609.35052v1

[OPIS: An Input-Grounded Benchmark for Multi-Object Memory in Video World Models](https://arxiv.org/abs/2609.35052v1)；首次提交 2026-09-28，所核对版本更新 2026-09-28。

- **收录角色**：Evaluation / OPIS。**载体**：Evaluation / Memory-oriented Benchmark（无新增 model carrier）。
- **AR 依据**：评测的 camera-driven group 包括 SANA-WM、LingBot-World2 等 AR world models；只纳入它们的历史依赖测试。 [PDF p.4](https://arxiv.org/pdf/2609.35052v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.35052v1#page=5), [PDF p.8](https://arxiv.org/pdf/2609.35052v1#page=8)；§3–4 protocol; §5.1 camera-driven model group。
- **保存 / 写入**：评测从输入历史建立固定 object inventory；它是 evaluator 的参照记录。
- **后续读取**：Presence / Identity / Structure 对生成 continuation 评测；AR camera-driven group 含 SANA-WM、LingBot-World2 等。
- **分类判断**：benchmark 测试已有生成模型记忆；固定评测 inventory 不能被登记成新 Entity-centric model memory。
- **本轮处理**：保留仅 benchmark；限定 AR camera-driven 模型与历史依赖子集。
- **解释边界**：重现子集依赖历史；整套短 continuation case 不都要求窗口外记忆，其他 I2V 模型不一并归 AR。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.35052v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.35052v1#page=5), [PDF p.8](https://arxiv.org/pdf/2609.35052v1#page=8)；§3.1; §4; §5.1 camera-driven models。

- **同论文 benchmark**：OPIS；从初始输入建立 object inventory，Presence/Identity/Structure 读出；历史依赖涉及重现等子集，不能宣称全部 case 都需窗口外记忆。 [§3.1; §4 (p.5); PDF p.4](https://arxiv.org/pdf/2609.35052v1#page=4)。

### 24. Geometry as Address (GEAR) — 2609.34722v1

[Geometry as Address: Routing Attention to Visual Memory for Long-Horizon Camera-Controlled Video Generation](https://arxiv.org/abs/2609.34722v1)；首次提交 2026-09-28，所核对版本更新 2026-09-28。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory；辅助 Spatial and Geometric States（visibility）。
- **AR 依据**：AR rollout 的历史 latent bank 按几何地址检索；Invisible Octree 跟踪可见性。 [PDF p.3](https://arxiv.org/pdf/2609.34722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34722v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34722v1#page=5)；§3.1–3.3。
- **保存 / 写入**：历史 bank 写入 latent 与相机；Invisible Octree 持久更新已观察/未观察的可见性证据。
- **后续读取**：AR generator 按几何地址检索 latent bank，并以 visibility 路由/筛选历史 attention。
- **分类判断**：外观来自观测 latent；可见性 octree 有独立坐标持久状态，因此保留 Explicit 副类。
- **本轮处理**：保留 VAE + Explicit；精确限定 octree 的语义。
- **解释边界**：visibility octree 不能等同完整外观或动态物体的 3D 世界模型。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2609.34722v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34722v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34722v1#page=5)；§3.1–3.3; latent bank; Invisible Octree。

### 25. WorldAttention — 2609.34606v1

[WorldAttention: An Efficient Attention Architecture for Interactive Video World Models](https://arxiv.org/abs/2609.34606v1)；首次提交 2026-09-28，所核对版本更新 2026-09-28。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：正文按 AR diffusion chunk-by-chunk 生成；Wan 转成 4-step causal-attention student。 [PDF p.3](https://arxiv.org/pdf/2609.34606v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34606v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.34606v1#page=6)；§3 overview; §4 setup。
- **保存 / 写入**：历史 chunks 的 KV 分页保存，跨 GPU / CPU / NVMe 形成 full backup。
- **后续读取**：两阶段先选 prompt 再选 pages，把相关历史加载给 causal student 的 attention。
- **分类判断**：历史对象是分页 KV；HSA 的 linear projection 是当前读取计算，未成为跨 rollout 的独立 recurrent state。
- **本轮处理**：保留 Cache；记录 active budget 与 full archive 分离。
- **解释边界**：活跃读取上下文有界，完整备份 archive 随历史增长。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2609.34606v1#page=3), [PDF p.4](https://arxiv.org/pdf/2609.34606v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.34606v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.34606v1#page=6)；§3.1–3.2; hierarchical cache; HSA; §4 setup。

### 26. In-Flight KV Cache (FlashForward) — 2609.32540v2

[In-Flight KV Cache with Clean Anchors for Faster Autoregressive Video Diffusion](https://arxiv.org/abs/2609.32540v2)；首次提交 2026-09-26，所核对版本更新 2026-09-30。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：planner 按块 AR；renderer 的历史依赖采用 chunk-wise causal mask / 顺序生成，同时条件于预先生成的双侧 anchor plan。 [PDF p.5](https://arxiv.org/pdf/2609.32540v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.32540v2#page=6)；§3.1 Eq. (2); planner and renderer。
- **保存 / 写入**：renderer 按 denoising stage 保存旧 chunk 的 KV bank B_k，按尾部窗口维护。
- **后续读取**：chunk-causal / AR renderer 读取历史 stage KV，同时接收 planner 预生成的双侧 clean anchors。
- **分类判断**：持久历史载体是 stage KV；anchors 是额外的规划条件。
- **本轮处理**：保留 Cache，并持续保留 README 的 two-sided-anchor 条件标注。
- **解释边界**：属于条件于完整 anchor plan 的 AR renderer；不能表述为仅过去可见的严格在线 causal 输入。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2609.32540v2#page=5), [PDF p.6](https://arxiv.org/pdf/2609.32540v2#page=6)；§3.1; Eq. (2); AR planner and renderer。

### 27. QuantWM — 2609.26425v3

[QuantWM: Temporally Consistent 2-Bit KV Cache Quantization for Video World Models](https://arxiv.org/abs/2609.26425v3)；首次提交 2026-09-22，所核对版本更新 2026-09-28。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：历史 K/V 量化供后续因果查询读取；实际包含 Causal Forcing 等 AR 模型。 [PDF p.4](https://arxiv.org/pdf/2609.26425v3#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26425v3#page=5), [PDF p.7](https://arxiv.org/pdf/2609.26425v3#page=7)；§4; §5.1 AR hosts。
- **保存 / 写入**：历史 K/V 低位量化；保存低秩 residual correction 的系数/基与 attention 统计。
- **后续读取**：未来 AR 查询从量化 KV 重构 attention，用 residual / centroid 校正消除偏差。
- **分类判断**：持续对象仍是量化缓存与其校正侧信息；离线/解析修复不把轨迹存进模型权重。
- **本轮处理**：保留 Cache；补 p.6 校正对象及 p.7 AR hosts；删去泛称“长时生成”实验。
- **解释边界**：正文主生成评测为 93 frames；时序量化一致性不是分钟级历史回忆证据。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.26425v3#page=4), [PDF p.5](https://arxiv.org/pdf/2609.26425v3#page=5), [PDF p.6](https://arxiv.org/pdf/2609.26425v3#page=6), [PDF p.7](https://arxiv.org/pdf/2609.26425v3#page=7)；§4.1–4.2; correction C; §5.1 AR hosts。

### 28. ZYT-World — 2609.21712v2

[ZYT-World: A Real-Time Controllable World Model for Closed-Loop Autonomous-Driving Simulation](https://arxiv.org/abs/2609.21712v2)；首次提交 2026-09-18，所核对版本更新 2026-09-22。

- **收录角色**：Forms / VAE-space Visual Memory。**载体**：VAE-space Visual Memory。
- **AR 依据**：AR 驾驶 student 保留从跨轨迹 memory logs 检索 observation latents 的 cross-attention 路径；bounded native KV 另行维护。 [PDF p.3](https://arxiv.org/pdf/2609.21712v2#page=3), [PDF p.7](https://arxiv.org/pdf/2609.21712v2#page=7), [PDF p.10](https://arxiv.org/pdf/2609.21712v2#page=10), [PDF p.14](https://arxiv.org/pdf/2609.21712v2#page=14), [PDF p.15](https://arxiv.org/pdf/2609.21712v2#page=15)；AR student; Figure 6; §3.6; §4.6。
- **保存 / 写入**：memory logs 提供预先记录的跨轨迹 observation latents；生成器另有 bounded native KV。
- **后续读取**：按空间选 3 个、时间选 1 个 log latent，以 residual cross-attention 注入；AR student 继承 memory path。
- **分类判断**：作者称 implicit memory，但检索内容保持观测 latent 对应关系，所以归 Visual / VAE。
- **本轮处理**：保留 VAE；把来源修正为 cross-trajectory memory logs，区分 native KV。
- **解释边界**：所核对段落没有建立生成 chunk 在线写回 log bank；收录依据是 AR generator 读取既有视觉记忆。
- **写读与分类出处**：[PDF p.3](https://arxiv.org/pdf/2609.21712v2#page=3), [PDF p.7](https://arxiv.org/pdf/2609.21712v2#page=7), [PDF p.10](https://arxiv.org/pdf/2609.21712v2#page=10), [PDF p.14](https://arxiv.org/pdf/2609.21712v2#page=14), [PDF p.15](https://arxiv.org/pdf/2609.21712v2#page=15)；AR student; Figure 6; §3.6; §4.6。

### 29. Recency Forcing — 2609.19729v1

[Recency Forcing: Bridging the Long-Horizon Gap in Autoregressive Video Generation](https://arxiv.org/abs/2609.19729v1)；首次提交 2026-09-17，所核对版本更新 2026-09-17。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：直接研究 AR generator 在长 rollout 时的 KV 淘汰及 recency 读取失配。 [PDF p.4](https://arxiv.org/pdf/2609.19729v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.19729v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.19729v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.19729v1#page=7)；§3.2–3.4; TRB/BAR and KV eviction mismatch。
- **保存 / 写入**：生成后保留 global / recent / history KV；history 区按窗口策略淘汰。
- **后续读取**：TRB 对 history 区施加 recency bias，BAR 以等价 attention 实现；global sink 与 recent 保持原规则。
- **分类判断**：运行时 cache reader 直接改变，适合保留 Forms / Cache，同时登记训练及免训练变体。
- **本轮处理**：保留 Cache；方法定位由 §4 修正为 §3.2–3.4；补 training-free 配置。
- **解释边界**：BAR attention 重写不构成参数载体；recency 处理不证明任意远期内容都被保存。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.19729v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.19729v1#page=5), [PDF p.6](https://arxiv.org/pdf/2609.19729v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.19729v1#page=7)；§3.2–3.4; TRB; BAR; setup。

### 30. AlayaVista — 2609.14462v1

[AlayaVista: Streaming World Modeling from Panoramic States to Perspective Video](https://arxiv.org/abs/2609.14462v1)；首次提交 2026-09-13，所核对版本更新 2026-09-13。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：全景 generator 在 chunk 内双向、跨 chunk 因果，后 chunk 读 generated panoramic features 的 K/V。 [PDF p.7](https://arxiv.org/pdf/2609.14462v1#page=7), [PDF p.9](https://arxiv.org/pdf/2609.14462v1#page=9), [PDF p.10](https://arxiv.org/pdf/2609.14462v1#page=10)；§3.3 chunk-causal evolution; §3.6.1; early cached-feature anchor。
- **保存 / 写入**：chunk-causal 全景 backbone 缓存已生成特征的 KV；初始历史受保护，早期 cached features 作为 sparse spectral anchor。
- **后续读取**：后续全景 chunks 读取历史 cache 与 early anchor；当前 panorama latent 另供 viewport renderer。
- **分类判断**：历史缓存与 protected early-feature reuse 给出实际持续内容；当前 panorama 不构成独立的历史 VAE bank。
- **本轮处理**：保留 Cache；补 p.9–10 beyond-local early-anchor 的依据。
- **解释边界**：这一路径不能被称为大位移下的全局空间地图记忆。
- **写读与分类出处**：[PDF p.7](https://arxiv.org/pdf/2609.14462v1#page=7), [PDF p.9](https://arxiv.org/pdf/2609.14462v1#page=9), [PDF p.10](https://arxiv.org/pdf/2609.14462v1#page=10)；§3.3; §3.6.1 Eq. (11); spectral anchor。

### 31. Causal Audit of Memory Specificity — 2609.12090v1

[Does Video Memory Use What It Retrieves? A Causal Audit of Memory Specificity](https://arxiv.org/abs/2609.12090v1)；首次提交 2026-09-10，所核对版本更新 2026-09-10。

- **收录角色**：Evaluation / Memory Diagnostics。**载体**：Evaluation / Memory Diagnostics（WorldMem generative arm）。
- **AR 依据**：仅取 WorldMem generative arm：Diffusion Forcing 的 past-frame bank 条件化生成，并实施 read-time 内容替换。 [PDF p.5](https://arxiv.org/pdf/2609.12090v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.12090v1#page=7)；§4.2 WorldMem; §5.5 Figure 3。
- **保存 / 写入**：沿用 WorldMem 原生 past-frame bank；生成诊断固定 bank 索引、pose 与读取接口。
- **后续读取**：用 donor、wrong-place、mean、zero 等读取内容替换，在相同 AR 生成路径比较 episode-specific evidence。
- **分类判断**：贡献是因果读取干预/诊断，属于 Evaluation；不产生新的 model carrier。
- **本轮处理**：保留诊断角色，限定 WorldMem 实验。
- **解释边界**：JEPA / SAM2 等 predictor / tracker 子实验分别属于其他研究对象。
- **写读与分类出处**：[PDF p.5](https://arxiv.org/pdf/2609.12090v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.12090v1#page=7)；§4.2 WorldMem; §5.5 Figure 3。

### 32. World in World (WiW) — 2609.11548v1

[World in World: Explore the World with World Models](https://arxiv.org/abs/2609.11548v1)；首次提交 2026-09-10，所核对版本更新 2026-09-10。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States。
- **AR 依据**：AR world model 将 finalized chunks 的逐层 clean K/V 归档，供未来 rollout 读取。 [PDF p.4](https://arxiv.org/pdf/2609.11548v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11548v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11548v1#page=7)；causal rollout; §3.4。
- **保存 / 写入**：被淘汰 finalized chunks 的 per-layer clean K/V 归档，附 pose/time；视觉证据在 inference 侧构造。
- **后续读取**：后续 causal-fast rollout 按相机/时间路由 archived evidence，并在 native attention 中附加证据。
- **分类判断**：archive payload 明确是 clean KV；clean visual state 一词不能据此改判像素/latent。
- **本轮处理**：Learning 修正为 training-free；全部 LingBot-World2 causal-fast 参数冻结，无新训练或控制 adapter。
- **解释边界**：source-video evidence 与 rollout archive 都经证据接口读取，按用途区分。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.11548v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11548v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11548v1#page=7)；causal rollout; §3.4; §4.1。

### 33. Uncertainty DMD — 2609.11265v1

[Uncertainty DMD: Restoring Diversity in Few-Step Autoregressive Video Distillation](https://arxiv.org/abs/2609.11265v1)；首次提交 2026-09-10，所核对版本更新 2026-09-10。

- **收录角色**：Forms / Attention-cache States。**载体**：Attention-cache States（stochastic cache writing）。
- **AR 依据**：历史 cache 递归构建；每块只在写入时扰动一次，此后固定供后续 AR steps 读取。 [PDF p.4](https://arxiv.org/pdf/2609.11265v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11265v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11265v1#page=7)；AR formulation; §4.2; Algorithm 1。
- **保存 / 写入**：clean latent 每 chunk 写入前扰动一次，KV encoder 编码并提交 cache；之后固定。
- **后续读取**：后续 AR denoising 从固定递归 cache 读取，而非每次重采样历史。
- **分类判断**：persistent writer 改变是 memory 贡献；临时 latent 是写入材料，实际读取存储是 KV。
- **本轮处理**：保留 Cache；把记忆贡献限定为 component B 的 stochastic cache writing。
- **解释边界**：component A 的 first-chunk timestep perturbation 单独登记；主实验约 5 秒。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.11265v1#page=4), [PDF p.6](https://arxiv.org/pdf/2609.11265v1#page=6), [PDF p.7](https://arxiv.org/pdf/2609.11265v1#page=7)；AR formulation; §4.2–4.3; Algorithm 1 line 16。

### 34. StateBench — 2609.03673v1

[Do Video Generators Track the World Across Segments? A Benchmark and Method for World-State Reasoning in Video Continuation](https://arxiv.org/abs/2609.03673v1)；首次提交 2026-09-03，所核对版本更新 2026-09-03。

- **收录角色**：Evaluation / StateBench。**载体**：Evaluation / StateBench（MAGI-1 AR arm；StateAgent 方法排除）。
- **AR 依据**：StateBench 的 native AR baseline 为 MAGI-1（§5.1 / Table 1）；仅纳入 AR 模型的跨段状态记忆评测。 [PDF p.4](https://arxiv.org/pdf/2609.03673v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.03673v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.03673v1#page=7), [PDF p.8](https://arxiv.org/pdf/2609.03673v1#page=8), [PDF p.13](https://arxiv.org/pdf/2609.03673v1#page=13)；§3 StateBench; §5.1; Table 1; Appendix A。
- **保存 / 写入**：benchmark 从历史与 reveal boundary 构造目标状态，题目覆盖 past-visible / occluded-process / complex-transition。
- **后续读取**：MAGI-1 以历史 continuation 暴露状态，评测 SES / SCS；StateAgent 的未来末帧条件 Wan 方法另列排除。
- **分类判断**：benchmark 检验 AR baseline 的跨段状态；benchmark/agent 的 state graph 不作为新 AR model carrier。
- **本轮处理**：短名显示为 StateBench；StateAgent 方法定位修正为 §4.4 Eq. (12)。
- **解释边界**：200 cases 的 protocol 可评多种架构；仅明确 MAGI-1 实验提供 AR scope 依据。
- **写读与分类出处**：[PDF p.4](https://arxiv.org/pdf/2609.03673v1#page=4), [PDF p.5](https://arxiv.org/pdf/2609.03673v1#page=5), [PDF p.7](https://arxiv.org/pdf/2609.03673v1#page=7), [PDF p.8](https://arxiv.org/pdf/2609.03673v1#page=8), [PDF p.13](https://arxiv.org/pdf/2609.03673v1#page=13)；§3.1–3.2 StateBench; §4.4 Eq. (12); §5.1; Table 1。

- **同论文 benchmark**：StateBench；200 cases，包含可见历史、遮挡过程和复杂状态转移；揭示边界测试状态续接。 [§3.1; Figure 2 (p.4); PDF p.5](https://arxiv.org/pdf/2609.03673v1#page=5)。

## 可复核文件

- [34 篇分类 checklist（CSV）](2026-10-11-classification-checklist.csv)：角色、载体、写读、判定、修正、边界、版本与出处。
- [本轮结构化记录（JSON）](2026-10-11-classification-recheck.json)：另含复核前分类、AR/记忆两项证据和 PDF SHA-256。
- [34 个 arXiv 页面再次核对](2026-10-11-primary-source-check.json)：访问状态、题名、页面可见版本与 HTML hash。
- [117 篇原始候选清单](2026-10-10-paper-checklist.csv)及[完整审查](2026-10-10-recent-papers-check.md)：已同步本轮修正。
- [上一轮 scope 撤回记录](2026-10-10-scope-recheck.md)：20 篇移出、StateAgent 改为仅 StateBench；本轮没有再加入这些方法。

页码采用 PDF 物理页码，从 1 开始；链接固定 arXiv 版本。本轮覆盖 34 篇新增的相关方法/协议段落。其余摘要候选、旧论文 revisions 与仓库历史方法保持各自的原核对级别；代码复现和实验重跑不在本次文献核对中。
