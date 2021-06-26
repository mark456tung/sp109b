在參數列+ -lm參數代表和lib.a連結
介紹linux的起源
講解07lib的glib2 glist(doublely link list) gslist(link list)
vim在linux應該算是必要學的東西 可以參考老師sp的筆記
講解07lib sqlite3
簡單介紹POSIX標準(泛unix系統都可以執行)
CMAKE用於跨平台
conan 相當於c語言版的 pip
講解08-01 file.c 裡面使用了linux的函式庫 
若要跨平台須加上根據不同平台使用不同的函式庫 (且命令列加參數 -D ex: -D__POSIX__)
#ifdef __PISIX__
...
...
#endif

#ifdef __WINDOWS__
...
...
#endif

#ifndef