div1.asm
The program divides 100 by 7 and uses both eax and ebx registers for the operation.

Flags
1. Carry flag is undefined because the DIV instruction does not define the carry flag.
2. Parity flag is undefined because DIV operation does not define it.
3. Auxilliary flag is set to 1 because the value existed in the flag even before the operation. The DIV operation does not define the carry flag.
4. Zero flag is undefined because DIV operation does not define it.
5. Sign flag is undefined because DIV operation does not define it.
6. Overflow flag is undefined because DIV operation does not define it.
7. Direction flag is cleared because DIV operation does not affect it.
8. Interrupt flag is set to 1 because the DIV instruction does not modify the flag. The setting enables maskable interrupts.

div2.asm
The program divides 50000 by 300 to get 166 remainder 200. The operation uses DX:AX to store the quotioent and the remainder. DX: Remainder, AX: Quotient.

Flags
1. Carry flag is undefined because the DIV instruction does not define the carry flag.
2. Parity flag is undefined because DIV operation does not define it.
3. Auxilliary flag is set to 1 because the value existed in the flag even before the operation. The DIV operation does not define the carry flag.
4. Zero flag is undefined because DIV operation does not define it.
5. Sign flag is undefined because DIV operation does not define it.
6. Overflow flag is undefined because DIV operation does not define it.
7. Direction flag is cleared because DIV operation does not affect it.
8. Interrupt flag is set to 1 because the DIV instruction does not modify the flag. The setting enables maskable interrupts.