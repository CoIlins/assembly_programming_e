# README02 file
section .text defines the section containing executable instructions. global _start makes _start visible.
```
section .text
    global _start
```
Execution begins at _start
```
_start:
```
When `call work` command is called, the return address of the next instruction  is pushed onto the stack and jumps to the work function. RSP decreases by 8 bytes.
```
call work
```
After the work function is executed, the program is terminated. This contains the code to exit the program where the exit system call is selected and the exit status set to 0.
```
mov rax, 60
xor rdi, rdi
syscall
```
The work function is executed. The value of RBP is pushed onto the stack. RSP decreases by 8 bytes.
```
work:
    push rbp
```
The value of RSP is copied into RBP.  It sets current stack pointer as the new base pointer.
```
mov rbp, rsp
```
The command subtracts 16 bytes from RSP. This allocates 16 bytes of space.
```
sub rsp, 16
```
Stores the value 100 in in memory location (RBP - 8).
```
mov qword [rbp - 8], 100
```
Stores the value 200 in in memory location (RBP - 16).
```
mov qword [rbp - 16], 200
```
The command retrieves 100 from the stack into RAX.
```
mov rax, [rbp - 8]
```

The command retrieves 200 from the stack into RAX.

```
mov rbx, [rbp - 16]
```

nop command is no operation command. The values do not change.
```
nop
```
The command copies the value of RBP into RSP. This deallocates 16 bytes which was allocated for the 2 values.This increases the value of RSP by 16 bytes.
```
mov rsp, rbp
```
The command retrieves the saved RBP value from the stack.RBP increases by 8 bytes.
```
pop rbp
```
The ret command pops the return address of mov rax, 60 instruction and transfers execution to the mov rax, 60 instruction.
```
ret
```

## Observations
The function executes the work() and terminates. The function sets original base pointer to the current stack pointer. The new stack pointer is obtained by adding 16 bytes to the current stack pointer to allocate 16 bytes of space. Values 100 and 200 are pushed into the stack. The values are stored in RAX and RBX registers. Current stack pointer value is set to current base pointer value hence deallocates 16 bytes of space. The original base pointer is obtained by popping value from the stack.