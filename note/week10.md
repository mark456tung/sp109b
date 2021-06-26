* 系統程式ch10 單行程與多工
* 08-02 race norace 
* deadlock
   * 要注意鎖定及解鎖的順序
* race mlti thread 會有競爭情況(C下降為組語後可能會有衝突)
輪詢 不適合多工
* 多工 中間會有中斷時間給os搶控制權 目前大部分os 都有用 循環分時排程
* thread 可以共用變數 process 不能共用(除非有用些特殊的功能)
* 邏輯位址 實體位址
    * 簡單來說cpu產生邏輯位址，並透過記憶體管理單元映射到實體位置
    * https://eng.libretexts.org/Courses/Delta_College/Operating_System%3A_The_Basics/07%3A_Memory/7.5%3A_Logical_vs_Physical_Address
* 分頁 
   * 作業系統將資料分成固定大小的區塊，不需要時移到輔助記憶體需要時再拿回來用
   * https://eng.libretexts.org/Courses/Delta_College/Operating_System%3A_The_Basics/07%3A_Memory/7.6%3A_Paging
