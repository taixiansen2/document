# 统计学习课堂展示选题建议

## 最终推荐选题

**保序预测（Conformal Prediction）与分布无关的不确定性量化**

参考论文：

1. Angelopoulos, A. N., & Bates, S. (2022). *A Gentle Introduction to Conformal Prediction and Distribution-Free Uncertainty Quantification*.
2. Lei, J., G'Sell, M., Rinaldo, A., Tibshirani, R. J., & Wasserman, L. (2018). *Distribution-Free Predictive Inference for Regression*.
3. Romano, Y., Patterson, E., & Candes, E. J. (2019). *Conformalized Quantile Regression*.
4. Romano, Y., Sesia, M., & Candes, E. J. (2020). *Classification with Valid and Adaptive Coverage*.
5. Tibshirani, R. J., Barber, R. F., Candes, E. J., & Ramdas, A. (2019). *Conformal Prediction Under Covariate Shift*.

## 为什么这个题目最适合

这个题目和“统计学习”课程高度相关，因为它同时涉及监督学习、泛化、校准、预测区间、分类决策和分布偏移等核心问题。它既不是单纯讲工程应用，也不是纯理论推导，难度比较适中，很适合三个人分工完成。

这个题目还有几个明显优势：

- **和别组题目不重合**：你给出的题目里没有小组专门讲“预测不确定性”或“分布无关置信保证”。
- **理论与应用兼具**：可以讲有限样本覆盖率、交换性等统计思想，也可以展示分类/回归中的实际预测区间或预测集。
- **结构清晰，适合展示**：可以自然拆成“基础思想 - 回归方法 - 分类与扩展”三部分，三个人分工很顺。
- **老师通常会觉得有深度**：它不是太基础的模型介绍，也不至于像纯高维理论那样推导过重。

## 建议的展示角度

不要把报告做成“5 篇论文逐篇汇报”，而是做成一个明确主题下的“文献串讲”：

**主线问题：模型给出一个点预测还不够，我们怎样在尽量少做分布假设的前提下，为预测结果附带可信的不确定性范围？**

围绕这个问题，可以依次讲：

1. 为什么传统点预测不够，为什么我们需要预测区间/预测集。
2. Conformal Prediction 的基本思想是什么，为什么它能给出有限样本保证。
3. 在回归里如何构造预测区间，普通 split conformal 和 CQR 有什么差别。
4. 在分类里如何输出“标签集合”而不是单一标签，并保证覆盖率。
5. 当训练集和测试集分布不完全一致时，为什么原方法会受影响，如何做 covariate shift 修正。

## 五篇论文的作用分工

### 1. 入门综述

**论文**：*A Gentle Introduction to Conformal Prediction and Distribution-Free Uncertainty Quantification*

**用途**：这篇最适合作为你们的理论引入和整体框架来源。它对概念解释很友好，适合做 PPT 的前半部分。

**建议讲点**：

- conformal prediction 的核心目标
- exchangeability / i.i.d. 背景
- calibration set 的作用
- coverage guarantee 的直观理解

### 2. 回归基础论文

**论文**：*Distribution-Free Predictive Inference for Regression*

**用途**：这篇是回归场景下非常经典的基础论文，可以用来解释 full conformal、split conformal 的基本思路，以及“分布无关覆盖率”这一统计保证。

**建议讲点**：

- 回归预测区间如何构造
- split conformal 为什么计算更快
- 有效性与区间长度之间的平衡

### 3. 最适合当主讲论文

**论文**：*Conformalized Quantile Regression*

**用途**：如果老师希望你们“围绕一篇论文重点展开”，最推荐以这篇为主论文。因为它比基础 conformal 更有方法创新，但又不至于太难。

**建议讲点**：

- 传统 conformal 在异方差数据上的不足
- quantile regression 与 conformal 的结合
- 为什么 CQR 的区间更自适应、更短
- 实验结果如何体现优势

### 4. 分类扩展论文

**论文**：*Classification with Valid and Adaptive Coverage*

**用途**：这篇可以把展示从回归自然扩展到分类。它非常适合课堂展示，因为“输出一个标签集合”这个想法很直观。

**建议讲点**：

- 分类任务中的 prediction set 是什么
- 单标签输出与集合输出的区别
- coverage 和 set size 的权衡

### 5. 进阶扩展论文

**论文**：*Conformal Prediction Under Covariate Shift*

**用途**：这篇适合作为最后的扩展讨论，体现你们不仅会讲基础方法，还知道它在真实场景中的限制和改进方向。

**建议讲点**：

- 为什么 covariate shift 会破坏原有保证
- weighted conformal 的基本思想
- 真实数据分布变化下的方法挑战

## 三人分工建议

### 成员一：背景与基本理论

- 介绍问题背景：为什么点预测不够
- 讲解 conformal prediction 的核心流程
- 说明 coverage guarantee 的直观意义

### 成员二：回归部分

- 介绍 split conformal regression
- 重点讲 *Conformalized Quantile Regression*
- 展示异方差数据下区间自适应的例子

### 成员三：分类与扩展

- 介绍分类 prediction sets
- 讲 covariate shift 下的 extension
- 做总结与开放问题讨论

## 推荐的 PPT 结构

1. 研究问题：为什么机器学习不仅要“预测准”，还要“知道自己不确定”
2. 基本思想：什么是 conformal prediction
3. 统计保证：为什么它能做到 distribution-free coverage
4. 回归方法：split conformal 与基本预测区间
5. 主论文：Conformalized Quantile Regression
6. 分类扩展：valid and adaptive coverage
7. 现实挑战：covariate shift
8. 总结：优点、局限和未来方向

## 如果老师要求“只选一篇论文重点讲”

优先选择：

**Conformalized Quantile Regression（参考论文 3）**

原因如下：

- 有明确的方法创新点
- 和统计学习课程中的回归、分位数、泛化都能挂钩
- 理论可以讲，实验也好讲
- 难度适中，适合课堂展示

## 可以直接采用的选题标题

你们最后可以从下面几个标题里选一个：

1. **保序预测：面向机器学习的分布无关不确定性量化**
2. **从回归到分类：Conformal Prediction 的方法与应用**
3. **带覆盖率保证的预测：Conformal Prediction 及其扩展**
4. **Conformalized Quantile Regression 及其在统计学习中的意义**

## 最终建议

如果你们想要一个“稳、好讲、老师容易认可”的展示方案，建议最终定为：

**选题：保序预测（Conformal Prediction）与分布无关的不确定性量化（参考论文：1, 2, 3, 4, 5）**

如果需要“围绕单篇论文展开”，则建议定为：

**选题：Conformalized Quantile Regression：带有限样本覆盖保证的自适应回归预测区间（参考论文：3，同时补充参考 1, 2, 4, 5）**