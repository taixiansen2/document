## 文献整理

### 1. Flash Boys 2.0: Frontrunning in Decentralized Exchanges, Miner Extractable Value, and Consensus Instability

- 作者：`Philip Daian et al.`
- 年份 / 来源：`2020`
- Venue / CCF：`IEEE S&P 2020`，`CCF-A`
- 核心问题：DEX 上的前跑、回跑和优先 gas 拍卖如何形成系统性 MEV 问题
- 方法：实证测量 + 机制分析，提出并推广 `MEV` 叙事
- 与 PropAMM 的关系：提供“透明排序环境下，执行质量如何被排序竞争吞噬”的奠基框架
- 链接：[IEEE](https://ieeexplore.ieee.org/document/9152675) | [DOI](https://doi.org/10.1109/SP40000.2020.00040) | [arXiv](https://arxiv.org/abs/1904.05234)

### 2. High-Frequency Trading on Decentralized On-Chain Exchanges

- 作者：`Liyi Zhou, Kaihua Qin, Christof Ferreira Torres, Duc V. Le, Arthur Gervais`
- 年份 / 来源：`2021`
- Venue / CCF：`IEEE S&P 2021`，`CCF-A`
- 核心问题：夹子攻击在链上 DEX 中如何形成、如何测量、如何影响用户
- 方法：形式化 sandwich 攻击并结合链上数据做实证分析
- 与 PropAMM 的关系：是理解对抗性流量、毒性订单、maker 保护机制的核心参考文献
- 链接：[DOI](https://doi.org/10.1109/SP40001.2021.00027) | [arXiv](https://arxiv.org/abs/2009.14021)

### 3. SoK: Decentralized Finance (DeFi) Attacks

- 作者：`Liyi Zhou et al.`
- 年份 / 来源：`2023`
- Venue / CCF：`IEEE S&P 2023`，`CCF-A`
- 核心问题：真实世界 DeFi 攻击和学术研究之间到底有哪些错位
- 方法：系统化梳理 `181` 起 DeFi 事故、学术论文与审计报告
- 与 PropAMM 的关系：可作为威胁模型与风险分类总表，帮助把 PropAMM 置于 DeFi 攻击面而不是孤立地讨论
- 链接：[IEEE](https://ieeexplore.ieee.org/document/10179435/) | [arXiv](https://arxiv.org/abs/2208.13035) | [ePrint](https://eprint.iacr.org/2022/1773)

### 4. A Large Scale Study of the Ethereum Arbitrage Ecosystem

- 作者：`Robert McLaughlin, Christopher Kruegel, Giovanni Vigna`
- 年份 / 来源：`2023`
- Venue / CCF：`USENIX Security 2023`，`CCF-A`
- 核心问题：以大规模测量方式刻画 Ethereum DEX 套利生态的规模、利润与安全外部性
- 方法：构造 arbitrage identification 和 opportunity detection 系统，对 28 个月数据做大规模分析
- 与 PropAMM 的关系：把“外部套利压力到底多大”从概念推进到数据层面，适合用来支撑 execution quality 的现实边界
- 链接：[USENIX](https://www.usenix.org/conference/usenixsecurity23/presentation/mclaughlin)

### 5. Automated Market Making and Loss-Versus-Rebalancing

- 作者：`Jason Milionis, Ciamac C. Moallemi, Tim Roughgarden, Anthony Lee Zhang`
- 年份 / 来源：`2022`，常见入口为 `arXiv`；DBLP 可检索为 `Quantifying Loss in Automated Market Makers`
- Venue / CCF：`DeFi@CCS 2022 / arXiv`，`非 CCF`
- 核心问题：如何量化 LP 因池内价格滞后而遭受的真实损失，而不是只谈“无常损失”
- 方法：提出 `LVR` 作为可计算量，建立 LP 被更快信息流“捡走旧报价”的统一刻画
- 与 PropAMM 的关系：为“为什么需要主动更新参数、缩短 stale quote 窗口”提供最直接的理论基准
- 链接：[arXiv](https://arxiv.org/abs/2208.06046) | [DBLP](https://dblp.org/rec/conf/ccs/MilionisMRZ22.html) | [DOI](https://doi.org/10.1145/3560832.3563441)

### 6. Improved Price Oracles: Constant Function Market Makers

- 作者：`Guillermo Angeris, Tarun Chitra`
- 年份 / 来源：`2020`
- Venue / CCF：`AFT 2020`，`非 CCF`
- 核心问题：在 CFMM 中，如何用更合理的 oracle / 价格报告机制改善报价有效性
- 方法：从 CFMM 统一框架讨论价格、储备安全性与可计算性质
- 与 PropAMM 的关系：PropAMM 大量依赖轻量价格更新；这篇是“oracle-based AMM”为何成立的重要理论入口
- 链接：[arXiv](https://arxiv.org/abs/2003.10001) | [DOI](https://doi.org/10.1145/3419614.3423251)

### 7. am-AMM: An Auction-Managed Automated Market Maker

- 作者：`Austin Adams, Ciamac C. Moallemi, Sara Reynolds, Dan Robinson`
- 年份 / 来源：`2024`
- Venue / CCF：`arXiv`，`非 CCF`
- 核心问题：能否通过“管理权拍卖 + 主动费率控制”来缓解被动 AMM 的逆向选择问题
- 方法：引入 auction-managed 的池管理者，让其在窗口内动态设定 swap fee
- 与 PropAMM 的关系：与“主动参数更新、私有执行逻辑、用机制控制 toxic flow”的 PropAMM 思路高度同构
- 链接：[arXiv](https://arxiv.org/abs/2403.03367)

### 8. Optimal Routing for Constant Function Market Makers

- 作者：`Guillermo Angeris, Alex Evans, Tarun Chitra, Stephen Boyd`
- 年份 / 来源：`2022`
- Venue / CCF：`EC 2022`，`非 CCF`
- 核心问题：在多池、多资产的 CFMM 网络中，如何最优拆分和路由一笔订单
- 方法：把路由问题写成凸优化；带固定成本时扩展到混合整数凸优化
- 与 PropAMM 的关系：为“Jupiter 为什么会把单笔订单拆到多个池”和“PropAMM 如何在聚合器里被比较”提供标准数学框架
- 链接：[arXiv](https://arxiv.org/abs/2204.05238) | [DOI](https://doi.org/10.1145/3490486.3538336)

### 9. An Efficient Algorithm for Optimal Routing Through Constant Function Market Makers

- 作者：`Theo Diamandis, Max Resnick, Tarun Chitra, Guillermo Angeris`
- 年份 / 来源：`2023`
- Venue / CCF：`FC 2023`，`CCF-C`
- 核心问题：如何把最优路由从理论模型推进到更接近真实网络规模的可解算法
- 方法：用分解算法提升复杂 CFMM 网络下的求解效率
- 与 PropAMM 的关系：对应“真实聚合器/solver 的可扩展求解器”视角，比上一篇更靠近工程实现
- 链接：[arXiv](https://arxiv.org/abs/2302.04938)

### 10. Execution Welfare Across Solver-based DEXes

- 作者：`Yuki Yuminaga, Dex Chen, Danning Sui`
- 年份 / 来源：`2025`
- Venue / CCF：`arXiv`，`非 CCF`
- 核心问题：solver-based DEX（如 CoW、1inch Fusion、UniswapX）到底是否改善了用户执行福利
- 方法：做跨协议实证比较，度量 `execution welfare / price improvement`
- 与 PropAMM 的关系：是把“成交质量”从口号变成可评价指标的近期关键材料，也能解释私有库存报价与 AMM 路由之间的差异
- 链接：[arXiv](https://arxiv.org/abs/2503.00738)
