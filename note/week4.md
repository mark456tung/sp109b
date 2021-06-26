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

