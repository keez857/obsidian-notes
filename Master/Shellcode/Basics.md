
### Moving values into register

This is accomplished using `mov`

example:
`mov rdx, 5`
this moves the value `5` into the `rdx` register


---

### Returning a value
`ret` will usually return whatever value is in `rax`


---

### Instruction pointer
At any point, the instruction being executed is stored in a register called the instruction pointer

`rip` 

sometimes known as a program counter `pc`

** To access `rip` 


---

### file descriptor

also refered to as 'fd' this is usually stdin(0), stdin(1), stderror(2)

---


### Registers (64-bit)
At a high level, these are like variables. About 8 general purpose 64-bit integers registers on amd64
32 bit registers begin with `E` and 64 bit reigsters begin with `R`

`rax`
accumulator register - used for storing operands and result data
when a function returns, it's return value is typically put in `rax`

`rbx`
base register - pointer to data

`rcx`
counter register - loop operations

`rdx`
data register - I/O pointer

`rdi`
destination index - data pointer for memory operations

`rsi`
source index - data pointer for memory operations

`rbp`
stack base point register

`rsp`
stack pointer register

---

## Instruction Pointer

- Contains the memory address of the NEXT instruction to be executed
- Read-only, can only control it indirectly
- Focus of most shellcoding, exploit research, etc,
- Control of instruction pointer grants control of execution
- Most RCE exploits consist of ways to place arbitrary values into the instruction pointer


---

## Assembly

- Low-level programming language (about as close as you can get to binary)
- Used to communicate with the microprocessor directly
- Specific to processor family (intel, ARM, MIPS, etc)
- Used for optimization of software, debugging, and other low level coding
- Gateway to understanding: memory/processor exploits, rev eng, shellcoding


---

## Architecture

- x86 - 32 bit reigsters, can only manage a theoretical max of 4GB RAM
- x86_64 - is an extension of original 32-but x86 architecture. 64 bit registers, can access up to 17 billion GB RAM


---

## Assembly Instruction Format

```
[label] mnemonic [operands] [;comment]
```

`label` - used to represent identifier or a constant

`mnemonic` - identifies purpose of statement (not required if a line contains only a label or a comment)

`operands` - specifies data to be manipulated (most instructions take two operands)

`comment` - text ignored by assembler


example
`add eax, ebc ; EAX = EAX+EBX`


add is the mnemonic, eax and ebc are the operands
this is intel architecture format
`add [dest], [source]` you would add `dest` and `source` and store into `dest`


---  


## stack

Stores temporary parameters, like variables/parameters in functions

Example would be inputting a username into a login page. The username is stored on the stack to be used by the program later on.


RETURN ADDRESS - when a new function is called the program creates a new stack frame.
At the bottom is a return address that tells the CPU where to go next.
