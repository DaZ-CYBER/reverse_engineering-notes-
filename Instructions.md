
Two Different Syntaxes for Assembly:
* Intel - Windows
* AT&T - Linux

* Immediate Values - (IM) constant data
	* Such as the number 12
* Register - RAX, RBX, R12, AL, etc.
* Memory/Memory Address - a location in memory
	* Ex: 0x7FFF842B

A semi-colon (";") is used to write a comment in Assembly.

`Format of instructions:
``(Instruction/Opcode/Mnemonic) <Destination Operand>, <Source Operand>

* MOV - Move/store the source operand into a destination.

````assembly
mov RAX, 5
````

* LEA - Load Effective Address - The same as a MOV except for addresses.
	* LEA does not dereference, and is commonly used to compute addresses (essentially find the location of an address).

````assembly
lea RAX, num1 ; num1 now has address of RAX

lea RAX, [struct+8] ; 8 bytes FROM start of structure

mov RBX, 5
lea RAX, [RBX+1] ; RAX has address of RBX + 1

````


PUSH - Push data ONTO the stack
```assembly
push RAX
```
* PUSHING will act as a copy, so an address such as RAX on the bottom of the stack will still contain the value it had before it was pushed.
* Used for saving data inside the register.

POP - Take data from the TOP of the stack and store it into a destination.
```assembly
pop RAX
```

# Arithmetic

INC - Increment
```assembly
mov RAX, 8
inc RAX
```
* Value of the data is increased by 1.
	* In the example here, RAX is first set to 8, After using the INC instruction, it will then be moved to 9.

DEC - Decrement
```assembly
mov RAX, 8
dec RAX
```
* Value of the data is decreased by 1.

ADD - Add a source to a destination
```assembly
mov RAX, 2
mov RBX, 3
add RAX, RBX
```
* Basically just "+=" in regular programming.
	* RAX is first set with a value of 2.
	* RBX is then set with a value of 3.
	* RAX = RAX + RBX (OR) RAX+=RBX
	* This will return a value of 5.

SUB - Substract a source from a destination
```assembly
mov RAX, 5
mov RBX, 3
sub RAX, RBX
```
* Same as "-=" in programming
	* Just like the above but the other way around.

MUL - Unsigned multiplication of two registers.
IMUL - Signed multiplication of two registers.
```assembly
mov RAX, 25
mov RBX, 5
mul RBX ; Multiplies RAX (25) with RBX (5)
```
* RDX:RAX
	* Whatever you want to multiply AS is stored in RAX.
	* Whatever you want to multiply WITH is stored in the variable you pass into MUL(in the above example, RBX).

DIV - Unsigned division of two registers.
IDIV - Signed division of two registers.
```assembly
mov RAX, 18
mov RBX, 3
div RBX ; Divides RAX (18) by RBX (3)
```
* Same as above but with division.

# Flow Control

RET - short for "return"
```assembly
mov RAX, 10 ret
```
* One of the purposes of RAX is to hold return values.
* In the above example, RAX is set to 10 and then returned from the function it is apart of.

CMP - compares two values and sets the Zero Flag (ZF) dependent on their result.
	* Zero Flag - If this flag is set to 1, that means that the value being compared was equal to the operand it is being compared to.
```assembly
mov RAX, 5
cmp RAX, 5
```

JCC Instructions - JNE, JLE, JNZ, and many more.
* JCC is not an instruction, but rather a collection of the instructions listed above.
	* JNE will jump if the comparison is not equal.
	* JLE will jump if less than or equal.
	* JG jumps if it is greater.*

````assembly
mov RAX, 5
cmp RAX, 5
jne 5 ; Jump to line 5 (ret) if not equal.
mov RBX, 10
ret
````

* The following example will return if RAX is not equal to the value it is compared to (in this case, 5).
* It will then jump to line 5 and SKIP `mov RBX, 10`

NOP - No Operation
* This instruction does jack shit.
* It's typically used for padding.

# Flipping Out

* Compilers will sometimes change code that might be different from what a regular programmer would write.
* This is the compiler's idea of efficiency.

Programmer Code:
````cpp
if(x == 4){
    func1();
}
else{
    return;
}
````

Compiler Code
````cpp
if(x != 4){
    goto __exit;
}
func1();
__exit:
return;
````

* The compiler generates this like this because it feels like this is the best way to write the code, and skips more code.
	* While it may not look efficient in the above example, in much larger examples the efficiency will be more apparent.

# Pointers

* Essentially used to get the value of a specific memory address.

````cpp
int main(){
    int num = 10;
    # num is equal to 10
    int* ptr = &num
    # ptr now holds the address of num
    return (*ptr + 5);
    # returns the value of ptr + 5
}
````

* ptr is a pointer to num
	* ptr is holding the memory address of num.

Square Brackets

* Dereference something in assembly.
	* [var] the address POINTED TO by var.
	* We essentially want to access the memory address that var is holding.
* LEA - Ignore everything about square brackets when woring with LEA. LEA is short for Load Effective Address and it's used for calculating and loading addresses.
	* With LEA instructions, square brackets do NOT dereference.
	* This is because LEA is only used to load and calculate ADDRESSES, not DATA.

```assembly
lea RAX, [var]
mov [RAX], 12
```

* var is loaded into RAX
	* RAX will now act as a pointer because we are working with LEA.
	* 12 is now moved into [var] since [var] is pointed to by RAX.

````assembly
mov num, 10 ; 10 goes into num
lea ptr, [num] ; ptr now points to num
mov rax, [ptr] ; the value of ptr(num) is moved into rax
add rax, 5 ; adds value of ptr(num) and 5
ret
````

* This is going to return 15.

````assembly
lea RAX, [RCX+8] ;This will add 8 to the address inside RCX, and set RAX to the resulting address.
````
````assembly
mov RAX, [RCX+8] ;This will add 8 to the address already held by RCX, then dereference the new address and put whatever is at that address into RAX.
````

Zero Extension
* Modifying the remaining bits with no values in a register to 0
	* Ex: If you moved a value into EAX should the upper 32-bits change?

* `movzx` performs this zero extension.

# JMP's Mason

For **_unsigned_** comparisons:

- JB/JNAE (CF = 1) ; Jump if below/not above or equal
    
- JAE/JNB (CF = 0) ; Jump if above or equal/not below
    
- JBE/JNA (CF = 1 or ZF = 1) ; Jump if below or equal/not above
    
- JA/JNBE (CF = 0 and ZF = 0); Jump if above/not below or equal

For **_signed_** comparisons:

JL/JNGE (SF <> OF) ; Jump if less/not greater or equal

JGE/JNL (SF = OF) ; Jump if greater or equal/not less

JLE/JNG (ZF = 1 or SF <> OF); Jump if less or equal/not greater

JG/JNLE (ZF = 0 and SF = OF); Jump if greater/not less or equal

