# Front-End_Compiler(前端編譯器)

110下程式語言與編譯器Programming Assignment1 - MiniJ
 
---

Use lex (or flex) and yacc (or bison) to implement a front end (including a lexical analyzer and a syntax recognizer) of the compiler for the MiniJ programming language, which is a simplified version of Java especially designed for a compiler construction project by Professor Chung Yung.

使用 flex 及 bison 完成 MiniJ 的前端編譯器。

---

### 開發環境版本

gcc (tdm64-1) 4.9.2

flex version 2.5.4

bison (GNU Bison) 2.4.1

---

### 作業過程說明

report的Test run results指令未分類檔案，在CMD打開根目錄打以下指令執行即可。

*註：須先自行在根目錄新增一個空資料夾，資料夾名generated。

1.
完成minij_lex.l、minij_parse.y

2.
使用flex把minij_lex.l編譯成minij_lex.c
```
flex -o./generated/minij_lex.c ./src/minij_lex.l
```

3.
使用bison把minij_parse.y編譯成minij_parse.c

使用bison產生minij_parse.h
```
bison -d –o ./generated/minij_parse.c ./src/minij_parse.y
```

4.
使用gcc把minij_lex.c編譯成minij_lex.o

使用gcc把minij_parse.c編譯成minij_parse.o

使用gcc把minij.c編譯成minij.o
```
gcc -c -I./include ./generated/minij_lex.c -o ./obj/minij_lex.o
gcc -c -I./include ./generated/minij_parse.c -o ./obj/minij_parse.o
gcc -c -I./include -I./generated ./src/minij.c -o ./obj/minij.o
```

5.
使用gcc link minij.o、minij_lex.o、minij_parse.o到minijparse.exe
```
gcc -o ./bin/mjparse.exe ./obj/minij.o ./obj/minij_lex.o ./obj/minij_parse.o
```

---

### 測試

```
cd bin
mjparse.exe<../test/test1.mj
mjparse.exe<../test/test2.mj
mjparse.exe<../test/test3.mj
```
