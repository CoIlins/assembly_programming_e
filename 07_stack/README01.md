# 01.asm README file
Execution starts from here.
```
section .text 
    global _start
```
Execution of the program starts at _start.
```
_start:
```
Register RAX is assigned value 100. RSP remains unchanged.
```
mov rax, 100
```
Register RBX is assigned value 200. RSP remains unchanged.
```
mov rbx, 200
```
push RAX command places value 100 (which was contained in RAX) on the stack and decreases RSP by 8 bytes.
```
push rax
```
push RBX command places value 200 (which was contained in RBX) on the stack and decreases RSP by another 8 bytes.
```
push rbx
```
nop command is a no operation command: nothing is done for one CPU cycle.
```    
nop
```
pop RCX removes 200 from the top of the stack and stored in RCX. RSP increases by 8 bytes.
```
pop rcx
```
pop rdx command removes 100 from the stack and stores 100 in rdx.
```    
pop rdx
```
nop command is a no operation command: nothing is done for one CPU cycle.
```     
nop
```
mov rax, 60 selects the 64-bit exit system call
```
mov rax, 60
```
This sets the exit status to 0.
```    
xor rdi, rdi
```
This terminates the program.
```    
syscall
```
## Observations
The stack uses a Last In First Out strategy where the last value pushed is the first one poped. RSP is used in stack operations as the stack pointer. When pushing, the value of RSP decreases by 8 bytes and when popping, the value increases by 8 bytes. Value 100 and 200 were pushed and popped from the stack. nop command is a no operation command where nothing is done for one CPU cycle.    