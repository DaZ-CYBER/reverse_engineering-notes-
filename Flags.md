
Flags are used to signify the result of a previously executed operation or comparison.

Flags Register
* x86 - EFLAGS
* x64 - RFLAGS

# Status Flags

* Zero Flag (ZF) - Set if the result of an operation is zero. Not set if the result of an operation is not zero.
	* ZF is generally the most important flag when comparing values (something that usually happens in functions)
* Carry Flag (CF) - Set if the last unsigned arithmetic operation carried (addition) or borrowed (subtraction) a bit beyond the register. It's also set when an operation would be negative if it wasn't for the operation being unsigned.
* Overflow Flag (OF) - Set if a signed arithmetic operation is too big for the register to contain.
* Sign Flag (SF) - Set if the result of an operation is negative.
* Adjust/Auxiliary Flag (AF) - Same as the carry flag but for Binary Coded Decimal (BCD) operations.
* Parity Flag (PF) - Set to 1 if the number of bits set in the last 8 bits is even. (10110100, PF=1; 10110101, PF=0)
* Trap Flag (TF) - Allows for single-stepping of programs.

[https://www.tech-recipes.com/rx/1239/assembly-flags/](https://www.tech-recipes.com/rx/1239/assembly-flags/)

