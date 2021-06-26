# Week6
* 老師的系統程式ch1
* 介紹如何從高階語言到機器語言
    * Source Code ->Lexer->syntax Analyzer->Semantic Analyzer->Intermedia Representation->Intermedia Representation->code genetator & optimizer ->Object Code 可以參考 https://www.spreered.com/compiler_for_dummies/
* 介紹一點智慧財展的觀念
* 目的檔分 .bss .text .data 三段(儲存格式TDBMS) 還有.global .extern 標記
    * 可參考 http://sp1.wikidot.com/elfobjfile
* 連結器用來重定位
    * 什麼是重定位?
        * cpu不斷的從內存中取出指令後執行，而確認欲運行程序的地址就稱為重定位
    * https://segmentfault.com/a/1190000016433947
* 分配記憶體包含機器自動分配的stack段(記憶體位址由高到低)和使用者手動請求(malloc等)的heap段(記憶體位址由低到高)
* 稍微講解04-02-03fib的組合語言