`start` start program with a breakpoint set on `main`. 

`starti` start a program with a breakpoint set on `_start`. 

`run` start program with no breakpoint set. 

`attach <PID>` attach to some other already running program. 

`core <PATH>` analyze the coredump of an already run program.

specify arguments `start <ARGV1> <ARGV2> <ARGVN> < <STDIN_PATH>`.

`continue`, or `c`, to continue program execution.

`info registers` values of all registers

`print` or `p` to print register: `p $rdi` in decimal, `p/x $rdi`

---

`x/<n><u><f> <address>` examine contents of mem. `<u>` is unit size; `<f>` is format; `<n>` number of elements
unit sizes: `b` 1 byte `h` 2 bytes `w` 4 bytes `g` 8 bytes
formats: `d` decimal `x` hex `s` string `i` instruction
examples: 
`x/8u $rip` print next 8 instructions; `x/16i main` first 16 instructions of main

`disassemble main` or `disas main` print all instructions of main

`x/16gx $rsp` first 16 values on stack

`x/gx $rbp-32` to print a local variable stored there

---

`stepi <n>` or `si` step entering calls or `<n>` instructions

`nexti <n>` or `ni` step one instruction or `<n>` instructions

`finish` to finish current function

`break *<address>` breakpoint

`display/<n><u><f>` example `display/8i $rip` will always show next 8 instructions; `display/4gx $rsp will always show first 4 values on stack

---

## Scripting with GDB

Execute a script with `gdb -x <path_to_script>`

```x.gdb
start
break *main+42
commands
  silent
  set $local_variable = *(unsigned long long*)($rbp-0x32)
  printf "Current value: %llx\n", $local_variable
  continue
end
continue

```


