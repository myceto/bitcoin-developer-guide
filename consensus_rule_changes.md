### 一致性規則變更 | Consensus Rule Changes

為了維持一致性，所有的完整節點使用相同的一致性規則驗證區塊。然後，有時為了加入新特性或者防治[網路](https://bitcoin.org/en/developer-guide#term-network)濫用一致性規則會被更改。當新的規則被實施後，會在一段時間內出現已更新節點遵循新的規則而未更新的節點遵循舊的規則，這導致兩種可能的一致性分歧的出現：

1. 一個區塊遵循新的一致性規則，它將被已更新節點接受而被未更新節點拒絕。例如，一個新的交易特性被用於區塊內部，那麼已更新節點便可以理解這一特性並接受它，但是未更新節點則因為它違背了舊的規則而拒絕了它。

2. 一個區塊違反了新的一致性規則而被已更新節點拒絕，但卻被未更新節點接受。例如，一個不合理的交易特性被用在一個區塊內，已更新的節點因為新規則拒絕了它，但未更新的節點遵循舊的規則所以接受了它。

在第一種情況中，即未更新節點拒絕的情況，從未更新節點獲取到區塊鏈資訊的挖礦軟體會拒絕從已更新節點獲取資料的挖礦軟體在同一條鏈條上構建區塊。這樣導致了永久性的分叉鏈，一條是已更新節點的，一條是未更新節點的，這被稱為[硬分叉](https://bitcoin.org/en/glossary/hard-fork)。

![硬分叉](./en-hard-fork.svg)

在第二種情況中，即已更新節點拒絕的情況，如果已更新節點掌握大部分的算力就有可能避免永久性分叉。在這種情況下，因為未更新節點會和已更新節點接受相同的區塊而使已更新節點構建了更長的鏈，這樣未更新節點便會接受更長的有效區塊鏈。這被稱作[軟分叉](https://bitcoin.org/en/glossary/soft-fork)。

![軟分叉](./en-soft-fork.svg)

儘管一個分叉在區塊鏈中是一個實實在在的分歧，但是對一致性規則的更改被經常描述為有可能出現軟分叉或者硬分叉。比如，“擴充套件區塊大小上限到 1 MB 需要一個硬分叉。”在這個例子中，一個區塊鏈的硬分叉並不是一定需要，但是他卻是一種可能的結果。

資源：[BIP16](https://github.com/bitcoin/bips/blob/master/bip-0016.mediawiki)，[BIP30](https://github.com/bitcoin/bips/blob/master/bip-0030.mediawiki) 和 [BIP34](https://github.com/bitcoin/bips/blob/master/bip-0034.mediawiki) 的實現被當作可能導致軟分叉的變更。[BIP50](https://github.com/bitcoin/bips/blob/master/bip-0050.mediawiki) 描述了一種意外的硬分叉（通過暫且對已更新節點降級來化解）和一種當暫且的降低被移除後的有意的硬分叉。由 Gavin Andresen 寫的一篇文件描繪[未來的規則更改該如何實現](https://gist.github.com/gavinandresen/2355445)。