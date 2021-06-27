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


