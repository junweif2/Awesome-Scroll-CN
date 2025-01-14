ETHPrague活动期间，Scroll的研究员 Toghrul Maharramov 发表了关于zkRollup中的排序器和证明者分离的演讲。

排序器按顺序处理交易，证明者负责计算零知识证明

在 zkRollup 中使用经典共识机制可以快速确认，保留MEV。但为 Rollup 实现弹性机制很复杂，需要在排序器故障时，可以确保交易连续性的备份机制。    

Based Rollup 使用 L1 排序器来构建和提交交易批次到 L1，与以太坊紧密整合，但确认时间较慢，取决于以太坊的最终确定性，并且MEV将存留在以太坊主网上。

在 zkRollup 中可以通过实现竞争机制激励证明者，来防止中心化和维护协议的弹性。但Nakamoto共识机制中的零知识证明缺乏随机性，导致效率最高的证明者总是胜出，可能危及协议的弹性。
   
在 Rollup 中，提出了类似以太坊 Gasper 的插槽分配方案，其中使用伪随机函数和计时器来决定每个插槽的证明者，并在所分配的证明者计时器失效后可以无需许可地回退。


在无需许可的系统中，激励区块提议者和构建者参与，需要采用提议者和构建者分离的方案（PBS）。

区块提议者是插槽的Leader，区块构建者在最高价拍卖机制下出价，由区块提议者选择相应的区块构建者。

在 zkRollup 中，排序器将作为插槽初始阶段的区块构建者角色，证明者将作为插槽初始阶段的区块提议者角色。
排序器构建区块并参加拍卖，证明者选择出价最高的区块并传播其签名，确保协议激励的公平分配。
随后排序器签署并揭示区块内容，确保协议激励由自由市场决定了公平分配。

该协议设计的优势是，允许通过将不同的证明者分配到不同的插槽并允许它们并行计算证明来增加 TPS，并且通过自由市场决定了收益分配的比例。

在排序器和证明者分离的方案下，我们的目标是构建一个简明、通用、高效、中立和去中心化的协议，其中验证者的成本更高，考虑到激励和去中心化的问题。

