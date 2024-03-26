
Windows x64 Calling Convention
* These calling conventions determine how information is passed into a function, which allocates space for variables and then cleans up the stack.
	* syscall, stdcall, fastcall, etc.
* This helps the compiler understand how to allocate data into the stack if it comes from libraries.
	* User-defined functions generally aren't difficult to allocate data to.*

Callee - Function being called
Caller - Function making the call

# Fastcall

* Windows uses a four-register fastcall calling convention by default.
* ABI - Application Binary Interface
	* Defines various rules for programs such as calling conventions, parameter handling, and more.
	* The first four parameters are passed in registers, LEFT to RIGHT.
		* NOT floating-point values, such as integers, pointers, and characters.

Integer parameters - RDX, RDX, R8, R9
Floating-point parameters - XMM0, XMM1, XMM2, XMM3
