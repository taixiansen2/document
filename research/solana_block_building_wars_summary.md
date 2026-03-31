# Solana 的区块构建战争 (Solana’s Block Building Wars)

*原文作者：Sam Schubert (发布于 Lightspeed)*
*原文链接：https://x.com/minnus/status/2023823017894133930*

## 一、文章主要内容总结

文章探讨了随着 Solana 链上交易量和专有做市商（PropAMM）的爆发，**区块到底由谁来构建、如何排序**成为了各方利益争夺的焦点。文章对比了当前两大主流区块构建器阵营——**Jito BAM** 与新兴的 **Harmonic**——在机制、速度以及对 DeFi 应用实际经济表现上的差异。

研究指出，这种区块构建器的竞争导致了 Solana 链上执行环境的碎片化，使得应用（特别是对延迟极其敏感的 PropAMM）的表现极不稳定。为了彻底解决这个问题，文章提出必须依靠协议级的 **MCP（多并发提议者）** 和 **ACE（应用控制执行）** 机制作为最终出路。

---

## 二、核心术语讲解

这篇文章大量使用了 MEV 和 Solana 市场微观结构的高级术语：

1. **Jito BAM (Block Auction Mechanism)**
   Jito 推出的区块拍卖与构建节点机制。它目前是 Solana 上的主流构建器，并支持通过 Plugins（插件）让开发者安全地介入交易排序。

2. **Harmonic**
   一个新兴的区块构建与聚合层挑战者。它的特点是采用 50 毫秒的“微区块拍卖（Microblock auctions）”，并承诺尊重防抢跑标签（"dontfront" / "dontbundle"）。

3. **Prop AMM (Proprietary AMM)**
   专有自动做市商（如 SolFi, GoonFi, HumidiFi 等）。它们不依赖散户注入资金，而是由专业团队自带库存，并通过极高频地提交链上**预言机更新（Oracle Update）**来调整价格，从而对抗套利者。

4. **Oracle Update Win Rates（预言机更新胜率）**
   指特定的 PropAMM 能够抢在某个区块（Slot）的**最前面**更新价格的成功率。赢了就能避免用“旧价格”接单而被套利。

5. **Markouts（盈亏标记/执行质量评估）**
   衡量做市商（PropAMM）接单质量的关键经济指标，即交易发生后一段时间内资产价格的走势：
   - **正值 (Positive Markout)**：成交后价格走向对做市商有利，说明对手盘是真实用户的“健康流量（Soft flow）”。
   - **负值 (Negative Markout)**：成交后价格走向对做市商不利，说明做市商遇到了“逆向选择（Adverse selection）”，被信息更快的套利者当了韭菜。

6. **MCP (Multiple Concurrent Proposers，多并发提议者)**
   一种正在开发中的 Solana 协议层升级，允许多个领导者在同一时段并行提交区块，以此来保证交易不被单一出块人审查或窃视。

7. **ACE (Application-Controlled Execution，应用控制执行)**
   被视为 MEV 问题的“终局”。它允许应用自己掌控自己的交易执行与排序规则，而不是把命运交给区块构建器。

---

## 三、文章逻辑梳理

作者的分析逻辑非常严密，按以下四部分展开：

1. **Part 1：描绘竞争格局（The Landscape）**
   开篇介绍目前正在对垒的 Jito BAM 与 Harmonic，列举了 Jito 是如何通过各类提案（JIP-28/31/33）巩固自己霸主地位的，以及 Harmonic 是如何通过免收费用、提供抗 MEV 保护来试图破局的。

2. **Part 2：重温物理限制（Solana’s Streaming Design）**
   简要回顾 Solana 特有的“碎块（Shreds）”和 Turbine 流式传输机制，解释为什么出块时间的微小差异会产生巨大的影响。

3. **Part 3：实证数据与经济影响（Optimal Block Building）**
   这是文章的高潮。通过真实链上数据对比两家：Jito BAM 出块更快、预言机更新更靠前；**从 Markout 来看，Jito 下的 PropAMM 普遍是正收益，而在 Harmonic 的区块中，像 GoonFi 这样的 PropAMM 遭遇了负收益（被套利）。**

4. **Part 4：走向终局（MCP）**
   因为现状是：随着出块器轮换，PropAMM 每一秒的命运都在被动切换。所以得出了必须走向 MCP 与 ACE 的结论，用底层协议强行拉齐这种“不一致性”。

---

## 四、文章提出的核心问题是什么？

1. **执行环境的不一致性与碎片化 (Inconsistency & Fragmentation)**
   不同的出块节点正在运行不同的区块构建器，导致同一个 DEX，在不同的 Slot（区块槽）里，其防被套利的能力天差地别。这让依赖微秒级反应的 PropAMM 无法提供稳定的流动性。

2. **垂直整合带来的公平性担忧 (Vertical Integration Concerns)**
   如果区块构建器（比如 Harmonic）与特定的做市商/应用（市场传言其与某些 PropAMM 关系密切）在背后是一伙的，他们就可以在自己的区块里“偏袒”自己的应用，人为操纵预言机的更新顺序。这种不透明的优先权严重破坏了竞争环境。

3. **生态成熟后的“协调困境”**
   早期的 Solana 很容易通过强有力的核心团队推行系统级升级。但随着网络成熟，由于触动了验证者（Validators）、区块构建器、做市商等各方高达上千万美元的利益，像 MCP 这种能解决根本问题的协议级升级，推进起来面临着巨大的阻力。