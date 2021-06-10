系統程式ch10 單行程與多工
08-02 race norace deadlock
race mlti thread 會有競爭情況(C下降為組語後可能會有衝突)
輪詢 不適合多工
多工 中間會有中斷時間給os搶控制權 目前大部分os 都有用 循環分時排程
thread 可以共用變數 process 不能共用(除非有用些特殊的功能)
邏輯位址 實體位址 分頁 重定位