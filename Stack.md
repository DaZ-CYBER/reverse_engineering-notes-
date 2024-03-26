
The Stack

- x86: esp/rsp register at the BOTTOM of the stack
- edp/rdp register at the TOP of the stack

- The stack grows in a downwards spiral, esp decrements by 4 (or 9 on 64-bit x86)

The stack is used primarily for these few things:
- Storing function arguments
- Storing local variables
- Storing processor state between function calls

say_hi called into a 32-bit x86 C program:

relevant assembly:





