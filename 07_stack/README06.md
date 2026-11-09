# README06

Execution starts from here. `BITS 32` tells NASM that the program uses 32-bit instructions and registers. The `.text` section contains the program instructions to be executed. `global _start` makes `_start` visible to the linker.

```asm
BITS 32
section .text
    global _start
```

Execution of the program starts at `_start`.

```asm
_start:
```

Hexadecimal value `11223344` is loaded into EAX, and `1234` is loaded into EBX. Both EAX and EBX are 32-bit registers.

```asm
mov eax, 0x11223344
mov ebx, 0x1234
```

This pushes the value `11223344` stored in EAX onto the stack. Since this is a 32-bit program, 4 bytes are stored on the stack. Therefore, ESP decreases by 4 bytes.

```asm
push eax
```

This pushes the value `1234` stored in EBX onto the stack, on top of `11223344`. Another 4 bytes are stored, so ESP decreases by 4 bytes.

```asm
push ebx
```

The NOP instruction does nothing. It does not change the stack or any register.

```asm
nop
```

This removes the value at the top of the stack (`1234`) and loads it into EBX. Since 4 bytes are removed from the stack, ESP increases by 4 bytes.

```asm
pop ebx
```

This removes the next value at the top of the stack (`11223344`) and loads it into EAX. ESP increases by another 4 bytes, returning to its original value before the PUSH operations.

```asm
pop eax
```

The 32-bit exit system call is selected by loading `1` into EAX. The exit status is set to `0` using `xor ebx, ebx`. The `int 0x80` instruction invokes the Linux kernel to execute the system call and terminate the program.

```asm
mov eax, 1
xor ebx, ebx
int 0x80
```

## Observations

The two hexadecimal values are loaded into EAX and EBX respectively. They are then pushed onto the stack in that order.

Each PUSH operation stores 4 bytes because this is a 32-bit program. Therefore, ESP decreases by 4 bytes for every value pushed onto the stack.

The stack follows the LIFO (Last In, First Out) principle. This means that the last value pushed onto the stack (`1234`) is the first value removed.

During the POP operations, `1234` is removed and loaded into EBX, followed by `11223344`, which is removed and loaded into EAX.

ESP increases by 4 bytes after each POP operation. After both values have been popped, ESP returns to its original position before the PUSH operations.

Finally, the program executes the 32-bit Linux exit system call using `int 0x80`, with an exit status of 0, and terminates successfully.