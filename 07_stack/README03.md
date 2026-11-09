# README03

Execution starts from here.
```
section .text 
    global _start
```
Execution of the program starts at _start.
```
_start:
```
The value 10 is assigned to RAX register.
```
mov rax, 10
```
The call calculate command pushes the return address (the memory address of the after_call instruction) onto the stack and jumps to the calculate function. RSP decreases by 8 bytes.
```
call calculate
```
The function adds 5 to the stored value (10) hence becomes 15. RSP remains unchanged.
```
calculate:
    add rax, 5
```
The ret command pops the return address from the stack and transfers execution back to the after_call instruction. RSP increases by 8 bytes.
```
ret
```
Here, after_call() is called. Nop - No operation after the call. RAX = 15
```
after_call:
    nop
```

The 64-bit exit system call is selected (mov rax, 60). The exit status is set to 0 (xor rdi, rdi). syscall requests the operating ststem to terminate the program.
```
mov rax, 60
xor rdi, rdi
syscall
```
## Observations
Value 10 is added to RAX. When the calculate function is called, the return address of the next instruction is pushed onto the stack and RSP decreases by 8 bytes. The calculate function adds 5 to the value in RAX, changing it from 10 to 15. The ret command pops the return address from the stack and transfers execution back to the instruction after the call command. RSP increases by 8 bytes and returns to its original value before the function call. The final value stored in RAX after the function returns is 15. The program then terminates with an exit status of 0. 




















