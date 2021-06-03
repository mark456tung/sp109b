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
* make  
* 系統程式:寫給工程師用的(偏底程)
* 系統軟體:大家通用的
* 簡譯式程式語言比編譯式的慢，不過軟體開發周期較短
* make clean 報錯 解決:在windows中 刪除要把rm改成del 參考 https://stackoverflow.com/questions/49384301/make-clean-failed-in-windows
所有的gcc含式庫都要+上libex 
在make中$^ 代表:的右側(依賴檔) $@ 代表:的左側(輸出) %代表所有的 ex: %.o 即所有的.o檔 -L要連結的含式庫 ./目前的資料夾底下
```
e clean
rm -f *.o *.exe run
process_begin: CreateProcess(NULL, rm -f *.o *.exe run, ...) failed.
make (e=2): 系統找不到指定的檔案。
make: *** [Makefile:11: clean] Error 2
```
ar是gcc 下所附設的一個壓縮含式庫 壓縮成.a檔
--------------------------------------------
什麼是連結(只編一部連結 做函式庫用
)
gitbash https://dev.to/andrewriveradev/how-to-set-git-bash-as-integrated-terminal-in-vscode-2k31 