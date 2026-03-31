# Solana 的专有 AMM 革命 (Solana’s Proprietary AMM Revolution)

*原文出处：Helius Blog (作者：Lostin)*
*原文链接：https://www.helius.dev/blog/solanas-proprietary-amm-revolution*

## 一、文章主要内容总结

本文探讨了 Solana 链上近期迅速崛起的一种全新流动性提供模式——**专有自动做市商（Proprietary AMMs，简称 PropAMMs）**。与传统的被动流动性池（如传统 AMM）不同，PropAMM 允许专业的做市商将核心交易逻辑和自有资金直接部署在链上，从而实现“主动流动性（Active Liquidity）”。

依靠 Solana 极低的交易费用、高吞吐量以及 Jupiter 等聚合器带来的庞大散户流量，PropAMM 能够以极低的成本进行高频的价格预言机更新。这种机制不仅消除了链下执行的延迟，还能提供比肩甚至超越中心化交易所（CEX）的极佳报价。目前，PropAMM 已经主导了 Solana 的核心交易对（如 SOL/USDC 交易量占比超过 60%），深刻重塑了链上的做市结构。

---

## 二、核心术语讲解

1. **PropAMM (Proprietary AMM，专有做市商)**
   一种由专业做市商全资拥有并运行的链上独立交易池。不同于允许散户无许可提供资金的传统 AMM，PropAMM 使用做市商的自有库存（Inventory），并且其代码通常是不开源的“黑盒”。
   
2. **Active vs. Passive Liquidity (主动流动性 vs 被动流动性)**
   - **被动流动性（如 Uniswap）**：资金放入池中后，价格曲线是静态的，只有在发生交易（通常是套利者行为）时，价格才会被动调整。
   - **主动流动性（PropAMM）**：独立于用户的交易活动，做市商会根据链下的真实市场价格，主动、持续且高频地更新链上的报价曲线。

3. **Lightweight Oracle Updates (轻量级预言机更新)**
   PropAMM 成功的技术关键。做市商通过极其精简的交易（如消耗极低的 Compute Units）高频向链上推送最新的参数或价格。因为占用的资源极少，这些更新交易可以轻易通过微小的优先费（Tip）排在普通交易前面，赋予做市商“取消或改价的优先权（Cancel Priority）”。

4. **Toxic Flow & Adverse Selection (有毒流量与逆向选择)**
   当链下价格发生剧烈变动时，链上的静态报价会变得“过时”。此时，信息和速度更快的套利者（机器流）会以这个过时的、对做市商不利的价格买走资产，这就叫逆向选择（或有毒流量）。PropAMM 极速的预言机更新就是为了防范这种行为。

5. **DEX Aggregators (去中心化交易所聚合器，如 Jupiter)**
   连接用户和各个 DEX 的路由引擎。PropAMM 极其依赖 Jupiter，因为聚合器能为它们带来大量真实的、非套利的“散户流量（Retail Flow）”，让做市商敢于给出极窄的买卖价差。

---

## 三、文章的逻辑梳理

文章的论证逻辑逐步深入，具体分为以下几个部分：

1. **现象引入 (Introduction)**
   指出 Solana 上的交易格局发生突变，SolFi、Obric、HumidiFi 等陌生的 PropAMM 迅速抢占市场份额。
2. **市场数据证实 (Trading Data)**
   通过链上数据展示 PropAMM 的庞大体量（日均交易量超 10 亿美元），并且点明了它们高度依赖 Jupiter 聚合器（超 90% 的流量来源于此）。
3. **运作机制拆解 (How do proprietary AMMs work?)**
   对比了“链上订单簿”的高昂维护成本，解释了 PropAMM 的巧妙之处：利用轻量级预言机更新，以低廉的成本高频调整一条连续的数学报价曲线。这让它们既有极高的资本效率，又能躲避套利者的狙击。
4. **生态结构的演变 (New Market Structure)**
   说明 Solana 的 DeFi 市场已经分化为两层：一层是为长尾资产（如土狗币）服务的传统公共 DEX；另一层是为核心蓝筹资产（SOL、稳定币）服务、由专业机构下场的 PropAMM。
5. **结论 (Conclusion)**
   总结 PropAMM 是真正的“区块链原生”金融创新，它不是自上而下的规划，而是 Solana 底层高性能架构与市场竞争自然催生的产物。

---

## 四、文章提出的核心问题与隐忧

尽管 PropAMM 带来了极高的执行效率和更优的用户报价，但文章也指出了该模式带来的几个深层问题：

1. **中心化与透明度缺失 (Black Boxes & Centralization)**
   现有的 PropAMM 几乎全部是闭源的“黑盒”。这违背了 DeFi 早期开源、透明的去中心化精神。普通用户无法验证这些合约的真实逻辑，高度依赖聚合器的审查与背书。
2. **做市商权力的过度集中**
   流动性不再由社区提供（散户无法做 LP 赚取手续费），而是集中在少数拥有强大算法和资本的华尔街级别专业机构手中。
3. **对单一聚合器的极度依赖 (Aggregator Dependency)**
   PropAMM 实际上无法直接获取用户，它们的生存命脉完全捏在 Jupiter 这样的聚合器手中。这让 Jupiter 成为了绝对的流量看门人（Arbiter of access），引发了对流量渠道过于集中的市场结构脆弱性的担忧。
4. **资产覆盖的局限性**
   由于 PropAMM 需要承担库存的绝对价格风险，并且依赖链下预言机，这种模式无法适用于缺乏链下定价的长尾高波动资产（如各类新发行的 Memecoin）。因此，它无法完全替代传统的被动 AMM。