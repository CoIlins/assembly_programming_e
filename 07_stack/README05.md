# README05

Execution starts from *here*. The .text section contains the program instructions to be executed. global _start makes _start visible to the linker.
```
section .text 
global _start
```
Execution of the program starts at _start.
```
_start:
```
Hexadecimal values 1122334455667788 are loaded into RAX and 1234 is loaded into RBX.
```
mov rax, 0x1122334455667788
mov rbx, 0x1234
```
This pushes 1122334455667788 in RAX into the stack. 8 bytes are stored since this is a 64-bit program and it uses 8 bytes for each value stored in the stack. Hence, RSP decreases by 8 bits.
```
push rax
```
This pushes the value 1234 in RBX into the stack - on top of 1122334455667788. RSP decreases by 8 bits.
```
push rbx
```
The NOP instruction does nothing. It does not change the stack or any register.
```    
nop
```
This removes the value on top of the stack (1234) and is loaded into RBX. RSP increases by 8 bytes.
```
pop rbx
```
This removes the value on top of the stack (1122334455667788) and is loaded into RAX. RSP increases by 8 bytes.
```   
pop rax
```
The 64-bit exit system call is selected (mov rax, 60). The exit status is set to 0 (xor rdi, rdi). syscall requests the operating system to terminate the program.
```
mov rax, 60
xor rdi, rdi
syscall
```
## Observations
The two hexadecimal values are loaded into RAX and RBX. They are then pushed into the stack. They are popped into RBX and RAX respectively.The program then terminates.
