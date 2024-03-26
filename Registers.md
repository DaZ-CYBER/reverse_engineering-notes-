
Registers

- A register is a location within the processor that is able to store data, much like RAM. Unlike RAM however, accesses to registers are effectively instantaneous, whereas reads from main memory can take hundreds of CPU cycles to return

- Registers can hold really any value that it takes from its input, whether that be addresses, mathematical operators, anything.

- x86 - rip and rsp: holds the address of the next instruction to execute and the address of the stack respectively

- rax: 64-bit register
- eax: 32-bit of rax
- ax: low 16 bits
- al: low 8 bits
- ah: high 8 bits of ax (bits 8-16 of rax)
 ----

General Purpose Registers - They all pretty much just hold variables.

- RAX - Known as the **accumulator register**. Often used to store the return value of a function.
- RBX - Sometimes known as the **base register**, not to be confused with the base pointer. Sometimes used as a base pointer for memory access.
- RDX - Sometimes known as the **data register**.
- RCX - Sometimes known as the **counter register**. Used as a loop counter.
- RSI - Known as the **source index**. Used as the source pointer in string operations.
- RDI - Known as the **destination index**. Used as the destination pointer in string operations.
- RSP - The **stack pointer**. Holds the address of the top of the stack.
- RBP - The **base pointer**. Holds the address of the base (bottom) of the stack.

* RIP - The Instruction Pointer (most important register)
	* The address of the NEXT line of code to be executed.
	* Only an instruction such as RET can influence this register.

Assembly - The end goal of a compiler, to translate high-level code into a language that the computer can understand.

````c
if(x == 4){
    func1();
}else{
    return;
}
````

````assembly
mov RAX, x
cmp RAX, 4
jne 5       ; Line 5 (ret)
call func1
ret
````


Register Break Downs

RAX - 64-bit
EAX - 32-bit
AX - 16-bit (has 2 lower portions)
* AH - Higher 8-bit
* AL - Lower 8-bit

"E" - Extended
"R" - Register
* "R" was newly introduced in x64, they are not on 32-bit systems.

# Data Types

* Floating Point Values - Floats and Doubles
* Integer Values - Integers, Booleans, Chars, Pointers, etc.

Floating Point Registers

* YMM0 - YMM15 (64-bit)
* XMM0 - XMM15 (32-bit)
* XMM are the lower half of the registers, similar to how EAX is to RAX.

[https://en.wikipedia.org/wiki/Advanced_Vector_Extensions](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions)

# Extra Registers

* R8-R15
	* Designed to be extra registers that are used by integer type values (not floats or doubles)
	* All lower bytes (32-bit, 16-bit, 8-bit) can be accessed by appending the letter "d", "w", or "b",
	* R8 - Full 64-bit (8 bytes) register.
	* R8D - Lower double word (4 bytes).
	* R8W - Lower word (2 bytes)
	* R8B - Lower byte


