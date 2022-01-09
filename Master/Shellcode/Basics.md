
### Moving values into register

This is accomplished using `mov`

example:
`mov rdx, 5`
this moves the value 5 into the `rdx` register


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


### Registers
Are like variables. About 8 general purpose 64-bit integers registers on amd64

`rax`
when a function returns, it's return value is typically put in `rax`

`rbx`

`rcx`

`rdx`

`rdi`

`rsi`

`rbp`

`rsp`

