# README04
This is a 32-bit program. section .text defines the section containing executable instructions. global _start makes _start visible.
```
BITS 32
section .text
    global _start
```
Execution begins at _start: .
```
_start:
```
The call work command pushes the return address of the next instruction onto the stack and jumps to the work function. ESP decreases by 4 bytes since this is a 32-bit program - it processes data in chunks of 32 bits.
```
call work
```
The work() is executed. The value of EBP is pushed onto the stack to save the base pointer. ESP decreases by 4 bytes because of the push.
```
work:
push ebp
```
The value of ESP is copied into EBP. It sets the current stack pointer as the new base pointer for the stack. ebp = old esp.
```
mov ebp, esp
```
The command subtracts 8 bytes from ESP. This allocates 8 bytes of stack space for two 4-byte local variables.
```    
sub esp, 8
```
Stores the value 100 in the memory location (EBP - 4). ESP remains unchanged.
```
mov dword [ebp - 4], 100
```
Stores the value 200 in the memory location (EBP - 8). ESP remains unchanged.
```    
mov dword [ebp - 8], 200
```
The command retrieves 100 from the stack into EAX. ESP remains unchanged.
The value 100 was stored in memory address [ebp - 4].
```
mov eax, [ebp - 4]
```
The command retrieves 200 from the stack into EBX. ESP remains unchanged. The value 200 was stored in memory address [ebp - 4].
```    
mov ebx, [ebp - 8]
```
The nop command is a no operation command. The values do not change and ESP remains unchanged.
```    
nop
```
The command copies the value of EBP into ESP. This deallocates the 8 bytes reserved for the two local variables. ESP increases by 8 bytes. 
```
mov esp, ebp
```
The command retrieves the saved EBP value from the stack and restores the previous base pointer. ESP increases by 4 bytes.
```    
pop ebp
```

The ret command pops the return address from the stack and transfers execution to the instruction immediately after call work. ESP increases by 4 bytes and returns to its value before the function call.
```    
ret
```

After the work function is executed, the program is terminated. EAX is assigned 1 to select the 32-bit Linux exit system call. EBX is set to 0 as the exit status. int 0x80 invokes the system call to terminate the program.
```
mov eax, 1
xor ebx, ebx
int 0x80
```

## Observations
ESP is the 32-bit stack pointer and EBP is the 32-bit base pointer. Each of the uses 4 bytesto store 1 data unit in a stack. When call work is executed, the return address of the next instruction is pushed onto the stack and ESP decreases by 4 bytes. The work function saves the original EBP value and sets the current ESP as the new base pointer. ESP is then decreased by 8 bytes to allocate space for two local variables. Values 100 and 200 are stored in memory locations EBP - 4 and EBP - 8 respectively. They are retrieved into EAX and EBX. The function deallocates the 8 bytes reserved for the local variables. The pop ebp command restores the original base pointer and ret pops the return address and transfers execution back to _start. ESP returns to its original value before the function call. The program then terminates with an exit status of 0.


