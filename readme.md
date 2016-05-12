#OSX Dynamic Function Hook
![](Demo.png)
It is a simple proof of concept to hook on the memory, and it works on OSX 10.11.4 (x86_x64) well at May 12, 2015. You can include my hotpatch.h and easily to hook any function.

#How it works?
e.g. Hooking the `puts` function

![](putsDisasm01.png)
This is the disassembly result of original `puts` function.
We want to let every thread walk to this function, and jump to another function. 

I make a simple payload on the begin of `puts` function:
![](putsDisasm02.png)
Let the content of register rax be the pointer of our fake function `movabs rax, ptr` in memory, and using `jmp rax` to jump back our fake function.