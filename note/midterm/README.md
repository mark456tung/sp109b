# 前言
* 此筆記內容"扣除code及code原有的註解"大部分原創
* 遇到的問題大多google解決，理解後以自己的想法註釋(所以可能有誤)並附上參考來源

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
* 什麼是連結(只編一部連結 做函式庫用)

* gitbash https://dev.to/andrewriveradev/how-to-set-git-bash-as-integrated-terminal-in-vscode-2k31 
# week2
* compiler-->(main.s)Assembler-->(main.o)Machine Language-->cpu
* 四個重要的
    * compiler
    * Assembler
    * Virtual Machine
    * OS
* Compiler
    * Syntax
       * Lexer
       * Parser
    * Semantic
    * Code Genration
    * IR(中間碼)
    * ASM
    * obj
* 自然語言無法完整的做出規範，可是程式語言可以!!!
講解 compiler 
00的
* genEnglish.c genExp.c 
此兩個程式碼 只要能理解老師另外寫的rlib就能理解 在老師所寫的註解下 再補了一些自己的註解及參考資料
```
// int randInt(int n):隨機傳回一個小於 n 的整數 (0,1,2..., n-1)
// 用法:randInt(5) 會傳回 0, 1, 2, 3, 4 其中之一
int randInt(int n)
{ // 隨機傳回一個小於 n 的整數 (0,1,2..., n-1)
  return rand() % n;
}

// int randChar(char *set):隨機傳回 set 中的一個字元
// 用法:randChar("0123456789") 會傳回一個隨機的數字
int randChar(char *set)
{                        // 隨機傳回 set 中的一個字元
  int len = strlen(set); // Strlen用來計算字串長度，要傳地址 http://tw.gitbook.net/c_standard_library/c_function_strlen.html
  int i = rand() % len;
  return set[i];
}

// int randSelect(char* array, int size):隨機傳回 array 中的一個字串
// 用法:randSelect({"dog", "cat"}, 2) 會傳回二選一的字串
char *randSelect(char *array[], int size)
{
  int i = rand() % size; // rand()隨機生成一個 不大於32767的數字 參考:http://tw.gitbook.net/c_standard_library/c_function_rand.html
  return array[i];
}

void timeSeed()
{
  long ltime = time(NULL); //time 返回自紀元（00:00:00 UTC1970年1月1日），以秒為單位的時間 參考:http://tw.gitbook.net/c_standard_library/c_function_time.html
  // printf("ltime=%ld\n", ltime);
  int stime = (unsigned)ltime / 2;
  srand(stime); //把前面生成的時間 丟進來當種子以仿造隨機的效果 參考:http://tw.gitbook.net/c_standard_library/c_function_srand.html
}
```

 * 01 exp0.c exp0hack.c exp0var.c
     * srtchr() strchr(str,c) str:待搜尋字串， c:欲搜尋的字元 http://tw.gitbook.net/c_standard_library/c_function_strchr.html
     * agrv命令行參數 http://tw.gitbook.net/cprogramming/c_command_line_arguments.html
* 老師網頁上03-compiler 有中文的章節可以參考

# week3
* 講解 lexer.c 及複習c pointer
    * fopen(filename, mode) filename文件名 mode訪問模式 返回FILE point http://tw.gitbook.net/c_standard_library/c_function_fopen.html
    * fread(ptr, size, nmemb, stream) ptr一塊point位置的最小值 size每次讀取的大小 nmemb長度 file文件指針，輸入流  返回元素總數 http://tw.gitbook.net/c_standard_library/c_function_fread.html
    * /fclose關閉文件 如果沒有關閉會怎樣? https://stackoverflow.com/questions/8175827/what-happens-if-i-dont-call-fclose-in-a-c-program
* 稍微看之後一下之後可能的難度(os.c)

* 介紹compiler.c 
# week4 
介紹一點x86(32位元) 組合語言 組譯後連結才可執行<br>
組語有GAS(AT&T 語法)和NASM(Intel 語法)<br>
 09-linux asm 01hello和02hola hola示範在組與中呼叫c library<br>
當初看01hello這個例子的時候一整個矇逼<br>
因為網路上大部分找到的都是 movl 或movq之類的語法<br>
後來在youtube直接搜尋 GAS GNU Assembler找到了<br>
 https://www.youtube.com/watch?v=5vC7gQuvWoE&list=PLhw53ohdQ4gEgeZLSYJ5aLOeA0k_xS05x<br>
將整個系列看完後 才對組語比較理解，也解答了為什麼是mov而不是movq或movl<br>
在64bit os mov = movq ,  即64bit = 8byte<br>
32bit os mov = movl ,  即32bit = 4byte<br>
另外 movb = 1byte movw = 2byte<br>

01hello
```
_start:
        # write(1, message, 13)
        mov     $1, %rax                # system call 1 is write     mov $value, %register 就是 register = value , rax=1是寫入
        mov     $1, %rdi                # file handle 1 is stdout    rdi = 1 標準輸出
        mov     $message, %rsi          # address of string to output  把message的位置傳入rsi
        mov     $13, %rdx               # number of bytes              rdx = 13 H,e,l,l,o, ,w,o,r,l,d,\n,0 傳入的字串長度
        syscall                         # invoke operating system to do the write

        # exit(0)
        mov     $60, %rax               # system call 60 is exit
        xor     %rdi, %rdi              # we want return code 0     也可寫mov $0, %rdi 讓rdi=0 即return 0
        syscall                         # invoke operating system to exit
message:
        .ascii  "Hello, world\n"

```
# Week5
multipass list 列出機器<br>
multipass launch -n sp109b -c 4 -m 4G -d 40G<br>
multipass shell sp109b<br>
系統程式 9 4 5 1 3(這裡的組合語言比較類似 arm的)<br>
asm 01 hack例子vm.c<br>
虛擬機會模擬指令集 模擬器則可能只有表面而已<br>
目前最常看到的虛擬機種類是寄生虛擬機(Hosted VM)<br>
虛擬機分成三種架構 記憶體機 暫存器機 堆疊機(幾乎沒有cpu是這樣設計的)<br>
Java的JVM虛擬機(堆疊機)<br>
06-02 pitifulvm<br>
QEMU可以在RISC-V上跑 ARM X86 反之亦然 速度大約只比原生慢兩到三倍<br>
稍微介紹c4(可以自我編譯)有內建堆疊虛擬機<br>
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
# week9
介紹一些程式大公司的淵源(被告與告) google和oracle --htc和apple
* 08-01 task.c vmem.c mem.c 
    * getpid()用來取得目前的行程id
    * malloc(100e6)申請大小為100e6的記憶體
* 在 posix上 大多數函式庫都不需要+l參數 
* pid(process) 行程代號(原則:一個正在跑的程式會有大於1個行程)
    * &在linux 代表背景執行 kill pid 把某個行程關掉
* 08-02 georeMary.c           需要加參數 -lpthread (連結ptherad這個函式庫)
* 在windows 灌MSYS2 可支援 posix
* thread 可以共用變數 process 不可以共用變數
    * program:尚未load入記憶體的 code
    * process:load 到記憶體中的 Program 
    * thread:process 下的單位
    * 可以把process 想像成工廠，而thread是工人
* 系統程式ch10s
* 一些台灣的程式聚會
    * hitcon 台灣駭客年會
    * 開源人年會 coscup
    * itcon 學生計算機年會
* nohup 關掉的時候程式不會停掉
    * ex: nohup /path/myprogram &
# Week10
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
# Week11
* 08-02 producerconsumer生產者消費者問題(測試有無死結)
哲學家用餐
* 講解一下期末報告的方向 ex:sehttpd 編譯器 kilo 等等sp_more_project 裡面的一些專案， 可以自己寫code最好，去分析別人的code也不錯
* 10-03-01 os.c
# week12
* 08-03-01 fork1.c fork2.c fork3.c 08-03-02 fork2
   * pid>0 parent, pid==0 child
* 03 execvp1.c   
  * 從main跳入後 after 不會執行
* 04 system.c mysystem1.c 
* 05 zombie.c parent 還活著 child 還沒被回收(殭屍行程)
* 08-04-01 echo. fecho.c
* 08-05-v1 v2 myshell.c
# Week13
* 08-04-00 io1.c
   * open(檔名,讀取模式)  
      * O_RDONLY: 以唯讀模式開啟 
      * O_WRONLY: 以唯寫模式開啟 
      * O_RDWR: 以讀寫模式開啟
   * read(fd, buffer, lan) 
      * return長度 
      * 從fd讀取len個字元到buffer
* 08-04-04 stderr1 2.c 
   * 2>error.txt 1>output.txt
   * 1標準輸出
   * 2標準錯誤
* 08-07 bolcking non blocking1.c
   * open加上 O_NONBLOCK參數
* 08-06 timetcp1、2
   * socket(domain, type, protocol)
      * domain 選擇通訊協定家族
         * AF_UNIX 
         * AF_INET 
         * AF_NS 
         * AF_IMPLINK
      * type socket類型
         * SOCK_STREAM  
         * SOCK_DGRAM 
         * SOCK_RAW 
         * SOCK_SEQPACKET
      * protocol 
         * 預設為0 
         * 但type為SOCK_RAW時需指定TCP/UDP/IP/ICMP
      * [Reference](http://www.tsnien.idv.tw/Internet_WebBook/chap8/8-5%20Socket%20%E5%BA%AB%E5%AD%98%E5%87%BD%E6%95%B8.html)
   * memset(str, c, n)把str中n個字替換為c
      * [Reference](http://tw.gitbook.net/c_standard_library/c_function_memset.html)
   * struct sockddr_in
      * [Reference](http://www.tsnien.idv.tw/Internet_WebBook/chap8/8-4%20Socket%20%E5%82%B3%E8%BC%B8%E4%BD%8D%E5%9D%80.html)
   * INADDR_ANY表示 監聽0.0.0.0 也就是所有的IP
   * htonl(),ntohl(),htons(),ntohs()
      * htonl()--"Host to Network Long"  Network Byte Order 高到低
      * ntohl()--"Network to Host Long"  Host Byte Order 不同主機HBO不同 
      * htons()--"Host to Network Short"
      * ntohs()--"Network to Host Short"   
      * [Reference](https://www.itread01.com/content/1544971156.html)
   * bind(fd, addressp, addrlen) ，
      * fd 為所欲連結之 Socket 的描述子，
      * addressp 包含有關 Socket 欲連接的環境參數，如 IP 位址及 TCP 埠口等
      * addrlen 表示 addressp 資料的長度 
      * 若成功會反回>0
   * listen(fd, qlen) 
      * qlen所能連接的最大數量 
      * 成功return 0;
   * accept(fd, peeradr, &peeradrlen) 
      * 成功時回傳Client端的Socket位址失敗回傳-1 
      * peeradr:server提供的位址，用來承接client端的Socket位址  
      * peeradrlen 傳入peenadr的長度
      * 問題:?為何這邊寫null:
         * 簡單的來說，因為我們不在乎地址
         * [Reference](https://stackoverflow.com/questions/49657313/why-does-the-accept-call-uses-an-empty-sockaddr-structure)
   * time ctime
      * time 00:00:00 UTC1970年1月1日到現在的秒數
      * ctime 把time換算成日曆時間
      * [Reference](http://tw.gitbook.net/c_standard_library/c_function_ctime.html)
   * snprintf(s,n,foramt) 
      * buf:指向一塊字串地址 
      * n:max ize 
      * format:format
      * 使用snprintf可以避免超出大小後 程序直接中止
      * [Reference](https://www.wongwonggoods.com/cplusplus/cpp_string_format/cpp-printf/#snprintf)
   * write(sd, buf, nbytes) 
      * sd:SocketID , 
      * buf:字元指標,
      * byytes字元長度

關於socket的部分大部分參考 翻轉工作室-[TCP/IP 協定與 Internet](http://www.tsnien.idv.tw/Internet_WebBook/Internet.html ) 後以自己的想法濃縮 
# Week14
* 08-06-05 hellowebserver.c 
   * 傳統會用多thread 去服務clinet 目前有epoll可以 用較高效能的web server(jserv)
* headprintserver htmlserver.c httpd.c htmlTreadServer
* 08-09(後來變08-A1) 00. 01.02.03. 04-01. 04-02
# Week15
* 08-08-02
   * mkfifo(path, mode)
      * path即檔案路徑
      * mode類似 S_IRWXU 用來給讀寫執行權限
   * strcmp(str1, str2)
      * 用來比較字串
      * str1<srt2 return <0
      * str1>str2 return 1
      * srt1=str2 return 0
      * http://tw.gitbook.net/c_standard_library/c_function_strcmp.html
    * fgets(str, n, stream)
      * 將stream輸入到str最多不超過n個字符
# Week16
* 09-c-02-02/03/04
# Week17
## RISC-V簡介
資料來源：[維基百科](https://zh.wikipedia.org/wiki/RISC-V)

* 簡介<br>
是一個基於精簡指令集（RISC）原則的開源指令集架構（ISA）<br>
RISC-V指令集可以自由地用於任何目的，允許任何人設計、製造和銷售RISC-V晶片和軟體而不必支付給任何公司專利費。<br>
RISC-V指令集的設計考慮了小型、快速、低功耗的現實情況來實做，但並沒有對特定的微架構做過度的設計。<br>
# Week18
## XV6
* xv6是在ANSI C中針對多處理器x86系統的Unix第六版的現代重新實現。它在麻省理工學院的作業系統工程（6.828）課程中用於教學目的。

![image](https://user-images.githubusercontent.com/62127656/123508237-b5509280-d6a0-11eb-9391-88206695f6d3.png)
>The Xv6 operating system, an open source OS developed for teaching purposes, based on a rewrite of the UNIX v6 kernel. As a tiny minimalist system, few features are available.

# 本專案僅學習使用 
[license](https://github.com/mark456tung/sp109b/blob/main/LICENSE.MD)



