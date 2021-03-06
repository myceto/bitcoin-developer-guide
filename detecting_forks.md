### 發現分叉 | Detecting Forks

在出現上面提到的兩種分叉中，未更新的節點都可能使用和釋出不正確的資訊，導致一些會出現經濟損失的情況。特別的，未更新的節點會傳播並接受那些被已更新節點認定為無效的交易，這些交易將永遠不會成為全網最長區塊鏈的一部分。未更新節點也可能拒絕傳播已被或將要被加到最佳區塊鏈的區塊和交易，這樣它們提供的就是不完整的資訊。

Bitcoin Core 包含了通過監控區塊鏈工作量證明而發現硬分叉的程式碼。如果一個未更新的節點接收到的區塊鏈頭證明至少有六個區塊比這個節點認定的最佳區塊鏈有更多的工作量證明，這個節點就會在 `getinfo` RPC 命令結果中報錯並且在開啟了 `-alertnotify` 時執行 `-alertnotify`。這提醒運營人員這個未更新節點無法切換到那個本應該是最佳的區塊鏈上去。

完整的節點同時會檢查區塊和交易的版本好。如果最近的幾個區塊或者交易的版本比節點使用的要高，這可以假定為該節點沒有在使用當前的一致性規則。Bitcoin Core 0.10.0 通過 `getinfo` RPC 命令報告這一情況，並且如果 `-alertnotify` 被設定了會執行 `-alertnotify`。

在以上的情況中，明顯地來自一個未使用當前一致性規則節點的區塊和交易資料是一定不應該被信賴的。

連線到完全節點的 SPV 客戶端可以通過連線多個完全節點確保他們在同一區塊高度來判定是否出現了硬分叉，要加上或減去一些賬戶的區塊因為存在交易的延時和陳舊的塊。如果出現了分叉，客戶端可以與具有短鏈的節點斷開連線。

SPV 客戶端最好也對區塊和資料的版本號增長做監控，從而確保它們在使用同樣的一致性規則處理接受交易和建立新的交易。