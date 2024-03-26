
* Bit is one binary digit, either 0 or 1
* Nibble is 4 bits
* Byte is 8 bits
* Word is 2 bytes
* Double word (DWORD) is 4 bytes
* Quad word (QWORD) is 8 bytes

Signed Numbers - Can be positive or negative (Need a sign to distinguish whether they are positive or whether they are negative)
Unsigned Numbers - Can only be positive

# Data Type Sizes

Char - 1 byte (8 bits)
Int - 16-bit, 32-bit, 64-bit.
	Usually 32-bit.
	Signed integers: One bit is used to specify whether the integer is positive or negative
		Signed Int
			16-bit: -32,768 to 32767
			32-bit: -2,147,483,648 to 2,147,483,647
			64-bit: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
		Unsigned Int
			Minimum is 0, maximum is twice that of a signed int
				Ex: 32-bit: 0 to 4,293,967,295
Bool - 1 byte
	Either needs to be 1 or 0 ; true or false

# DATA POSITIONS / OFFSETS

Data Positions - Referenced by how far away they are from the address of the first byte of data.
* First byte of data is known as the BASE ADDRESS

12345678
1 - 0x0
2 - 0x2
3 - 0x4
4 - 0x6
