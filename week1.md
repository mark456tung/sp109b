# Week 1
* 可能會使用到工具/能力
   * C/C++/Rust
   * gcc/make/git/bash/msys2/Linux
* 教學所用的cpu架構
   * Hackcpu/x86/Risc-V

* 在vscode 裡輸入 $gcc hello.c -o hello (若不加-o 會出現a.exe 或a.out 的檔案)
* 然後./hello 執行 hello.exe (./即當前的資料夾)
* gcc -c fib.c -o fib (只編譯，不連結)
* gcc -S fib.c -f fib.s (輸出組合語言)
* 根據不同的編譯器及及不同的電腦 會產生不同的組合語言
* g++ hello.cpp -o hello (編譯c++)
* make  有點類似寫有點類似寫
* 系統程式:寫給工程師用的(偏底程)
* 系統軟體:大家通用的
* 簡譯式程式語言比編譯式的慢，不過軟體開發周期較短