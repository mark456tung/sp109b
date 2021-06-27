# HW2
## file
## code
* 參考if跟while寫出
    * skip for ()
    * 其餘部分與whie相似
```
void FOR() { 
  int forBegin = nextLabel(); //開始的label
  int forEnd = nextLabel();   //結束的label
  emit("(L%d)\n",forBegin);
  skip("for");
  skip("(");
  ASSIGN();                  //i = 0; 
  int e2 = E();              //i <= 10; 
  emit("if not t%d goto L%d\n",e2,forEnd);
  skip(";");
  int e3 = E();
  skip(")");
  STMT();
  emit("goto L%d\n",forBegin);
  emit("(L%d)\n",forEnd);
}
```
* make
* ./compiler test/for.c
## result
```

for(i=0;i<=5;i++){
        a=a+1;
}
========== lex ==============
token=for
token=(
token=i
token==
token=0
token=;
token=i
token=<=
token=5 
token=; 
token=i 
token=++
token=) 
token={
token=a
token==
token=a
token=+
token=1
token=;
token=}
========== dump ==============
0:for
1:(
2:i
3:=
4:0
5:;
6:i
7:<=
8:5
9:;
10:i
11:++
12:)
13:{
14:a
15:=
16:a
17:+
18:1
19:;
20:}
============ parse =============
skip(=) got ( fail!
Assertion failed: 0, file compiler.c, line 36
```