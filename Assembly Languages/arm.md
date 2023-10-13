
# ARM Assembly Cheat Sheet
Registers:

R0 to R15: General-purpose registers.
R13 (SP) and R14 (LR): Stack Pointer and Link Register.
PC: Program Counter.
Instructions:

MOV, ADD, SUB, MUL, CMP, B: Similar to x86.
LDR, STR: Load and store data from/to memory.
BL: Branch with Link (function call).
BEQ, BNE, BGT, BLT: Branch instructions based on condition codes.
SWI: Software interrupt for system calls.
Memory Access:

[address]: Access memory at the specified address.
[register, #offset]: Access memory using a base register and an offset.
[register, register, LSL #shift]: Shifted register addressing.
Stack Operations:

ARM stack operations are register-based, similar to x86 and x64.