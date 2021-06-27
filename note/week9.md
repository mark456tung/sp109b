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