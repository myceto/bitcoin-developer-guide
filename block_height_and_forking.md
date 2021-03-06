### 區塊高度及分叉 | Block Height And Forking

任何成功計算出那個比目標閾值低的區塊頭雜湊值的礦工，都可以將這整個區塊加到區塊鏈中（假設這個區塊是有效的）。這些區塊通常是通過區塊高度來定位的，所謂區塊高度是指某個區塊與比特幣第一個區塊（及區塊 0，眾所周知的創世區塊）之間的區塊個數。比如，區塊 2016 就是第一次難度調整的位置。

![比特幣分叉](en-blockchain-fork.svg)

多個區塊可以具有同樣的區塊高度，這在兩個或更多的礦工同時建立一個區塊時是很常見的。這導致瞭如上圖所示的明顯的分叉。

最終，礦工會產出一個新的區塊，它附加在且僅附加在同時被挖出的區塊中的一個之後。這樣使得某一個分叉比其他分叉更為健壯。假設一個分叉只包括有效的區塊，普通的節點總是跟隨更長的鏈，而放棄陳舊的短的分叉。（陳舊的區塊常常被叫做孤鏈，但是該術語也被用於描述確實沒有父區塊的區塊。）

如果一些礦工有其他的意圖，長期的分叉是有可能出現的，比如一些礦工在延續區塊鏈工作，而同時另一些礦工試圖通過發起 51％ 攻擊篡改交易紀錄。

因為多個區塊可以在區塊鏈分叉時具有同樣的區塊高度，所以區塊高度不應該用來做全局的唯一標示符。通常，區塊使用區塊頭的雜湊值來做標示（大多數時候是位元組倒序的十六進位制表示）。