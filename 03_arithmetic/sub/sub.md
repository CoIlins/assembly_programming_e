sub1.asm
The program moves value 50 into al and subtracts 80 from it to obtain -30 (11100010).However, this is shown as 226 in the register al.

Flags
1. The carry flag is set to 1 because the subtraction required a carry in order to be successful. 50 is smaller than 80 hence the carry was necessary.
2. Parity flag is set to 1 since the result (11100010) contains an even number of 1's (4 one's).
3. The auxiliary carry flag is cleared because there is no borrow from D4 to D3 during subtraction.
4. Zero flag is cleared since the result is a non-zero (11100010).
5. Sign flag is set to 1 since the most significant bit of the result is 1. (11100010).
6. Overflow flag is cleared since the result -30 lies within the range of -128 to 127.
7. Direction Flag is cleared because the SUB instruction does not affect the direction flag.
8. The interrupt flag is set to 1. The instruction does not modify it. The setting enables maskable interrupts.

sub2.asm
The program sub2.asm moves double word 1000 into register ax. Double word 2000 is subtracted from 1000 in the same register which results into -1000 (1111 1100 0001 1000)

Flags
1. The carry flag is set to 1 because the subtraction required a carry in order to be successful. 1000 is smaller than 2000 hence the carry was necessary.
2. Parity flag is set to 1 since the result (1111 1100 0001 1000) contains an even number of 1's (8 one's).
3. The auxiliary carry flag is cleared because there is no borrow from D4 to D3 during subtraction.
4. Zero flag is cleared since the result is a non-zero (1111 1100 0001 1000).
5. Sign flag is set to 1 since the most significant bit of the result is 1. (1111 1100 0001 1000).
6. Overflow flag is cleared since the result -1000 lies within the range of -32768 to 32767.
7. Direction Flag is cleared because the SUB instruction does not affect the direction flag.
8. The interrupt flag is set to 1. The instruction does not modify it. The setting enables maskable interrupts.