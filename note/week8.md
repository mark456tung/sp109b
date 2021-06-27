# Week8
在參數列+ -lm參數代表和lib.a連結<br>
介紹linux的起源<br>
* 講解07lib的glib2 glist(doublely link list) gslist(link list)<br>
    * link list 
        * a->b->c->d<br>
    * doublely link list
        * ->a->b->c<br>
        &nbsp;&nbsp;&nbsp;&nbsp;a<-b<-c<br>

* vim在linux應該算是必要學的東西 可以參考老師sp的筆記 
    * http://programmermedia.org/root/%E9%99%B3%E9%8D%BE%E8%AA%A0/%E8%AA%B2%E7%A8%8B/%E7%B3%BB%E7%B5%B1%E7%A8%8B%E5%BC%8F/01-sp/vim%E7%B7%A8%E8%BC%AF%E5%99%A8.md
* 講解07lib sqlite3
* 簡單介紹POSIX標準(泛unix系統都可以執行)
* CMAKE用於跨平台
* conan 相當於c語言版的 pip
* 講解08-01 file.c 裡面使用了linux的函式庫 
* 若要跨平台須加上根據不同平台使用不同的函式庫 (且命令列加參數 -D ex: -D__POSIX__)
```
#ifdef __PISIX__
...
...
#endif

#ifdef __WINDOWS__
...
...
#endif

#ifndef
```