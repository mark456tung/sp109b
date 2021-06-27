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