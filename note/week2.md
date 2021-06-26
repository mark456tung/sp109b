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