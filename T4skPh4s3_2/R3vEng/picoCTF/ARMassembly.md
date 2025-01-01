# ARMssembly 0
All I had to do is run the Assembly code with the arguments.

I compiled the code using 
```
aarch64-linux-gnu-as -o chall.o chall.S
aarch64-linux-gnu-gcc -static -o chall chall.o
```
After that I ran the chal with arguments using `qemu aarch64`
```
(base) kali@LordSensDomain:~/skibidi$ qemu-aarch64 ./chall 266134863 1592237099
Result: 1592237099
```
We convert `1592237099` into hex, remove `0x` which converts into `5ee79c2b`, thus our flag.
> FLAG -> picoCTF{5ee79c2b}

# ARMssembly 1
We are given the following ARM assembly code.  
```
        .arch armv8-a
        .file   "chall_1.c"
        .text
        .align  2
        .global func
        .type   func, %function
func:
        sub     sp, sp, #32
        str     w0, [sp, 12]
        mov     w0, 85
        str     w0, [sp, 16]
        mov     w0, 6
        str     w0, [sp, 20]
        mov     w0, 3
        str     w0, [sp, 24]
        ldr     w0, [sp, 20]
        ldr     w1, [sp, 16]
        lsl     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 24]
        sdiv    w0, w1, w0
        str     w0, [sp, 28]
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 12]
        sub     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w0, [sp, 28]
        add     sp, sp, 32
        ret
        .size   func, .-func
        .section        .rodata
        .align  3
.LC0:
        .string "You win!"
        .align  3
.LC1:
        .string "You Lose :("
        .text
        .align  2
        .global main
        .type   main, %function
main:
        stp     x29, x30, [sp, -48]!
        add     x29, sp, 0
        str     w0, [x29, 28]
        str     x1, [x29, 16]
        ldr     x0, [x29, 16]
        add     x0, x0, 8
        ldr     x0, [x0]
        bl      atoi
        str     w0, [x29, 44]
        ldr     w0, [x29, 44]
        bl      func
        cmp     w0, 0
        bne     .L4
        adrp    x0, .LC0
        add     x0, x0, :lo12:.LC0
        bl      puts
        b       .L6
.L4:
        adrp    x0, .LC1
        add     x0, x0, :lo12:.LC1
        bl      puts
.L6:
        nop
        ldp     x29, x30, [sp], 48
        ret
        .size   main, .-main
        .ident  "GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
        .section        .note.GNU-stack,"",@progbits
```

First we are storing 85, 6 and 3 on the stack.  
Then in first operation we load 85 and 6 (w1 and w0) and we left shift the bit by 6 to get w0 = 5440.  
Then we load 272 and 3 (w0 and w1) and we divide 5440 by 3 to get 1813. So the required value be `hex(1813) = 75` to WIN.  
> FLAG -> picoCTF{00000715}
