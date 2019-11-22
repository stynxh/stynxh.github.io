---
layout: post
published: true
title: simple guide the pwndbg
date: '2019-11-22'
category:
  - research
tags:
  - gdb
  - pwndbg
---
## install the pwndbg
```
git clone https://github.com/pwndbg/pwndbg.git
cd pwndbg
./setup.sh
```

## gdb with python
1. argument
```
(gdb)run $(python -c 'print "A" * 200')
```

2. standard input
```
(gdb) r <<< $(python -c 'print "A"*1')
```

## breakpoint
```
disassemble main
b *main+13
b function
info b
delete br 1
```

### memory display
```
x / [Format] [Address]
x / [Length] [Format] [Address]
x/5x 0x08041680
x/s $r0
x/3i 0x08041680

o(octal), x(hex), d(decimal), u(unsigned decimal),
t(binary), f(float), a(address), i(instruction), c(char), s(string)
and z(hex, zero padded on the left).
```

### watchpoint
```
watch $eax     >>>   let me know when eax is changed
watch $8012345
info watchpoints
```

### fork child process
```
set follow-fork-mode child
```

## display
```
display xx
undisplay xx
```

## run
```
run
si       >>>    excute current instruction. step into the function.
ni       >>>    excute current instruction. step over the function.
finish   >>>    excute and exit current function.
```
