add1.asm
The program adds 120 and 10 into al register, which is 01111000 + 00001010 = 10000010
The value 130 is moved to result.

Flags
1. Carry Flag cleared because there is no carry from the addition of the two numbers.
2 Parity flag is set to 1 since there is an even number of one's in the result (2)
3. Auxiliary carry flag is set to 1 because the lower nibble generates a carry to D4 during addition.
4. Zero flag is cleared since the result is a non-zero integer: 130.
5. Sign flag is set to 1 since the most significant bit is 1.
6. Overflow flag is set to 1 since the result is out of range for signed numbers (+127 to -128) therefore it is interprated as a negative value.
7. Direction flag is cleared since the add instruction does not affect the direction flag.
8. The interrupt flag is set to 1. The instruction does not modify it. The setting enables maskable interrupts.

add2.asm
The program moves 32000 into register ax and andds 500 to it.The value is moved to result.

Flags
1. Carry Flag is cleared because there is no carry genereted from the addition of the 2 numbers.
2. Parity Flag is cleared  since the lower 8 bits of the result contains an odd number of 1's (5).
3. Auxiliary Carry Flag is cleared since there is no carry generated from D3 to D4.
4. Zero Flag is cleared since the result is a non-zero integer: 32500.
5. Sign Flag is cleared since the most significant bit of the 16-bit result is 0 hence the result is positive.
6. Overflow Flag is cleared because adding 32000 and 500 results to 32500 which is within the 16-bit range of -32768 to +32767.
7. Direction Flag is cleared because the ADD instruction does not affect the direction flag.
8. The interrupt flag is set to 1. The instruction does not modify it. The setting enables maskable interrupts.
