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
Then we load 5440 and 3 (w0 and w1) and we divide 5440 by 3 to get 1813. So the required value be `hex(1813) = 75` to WIN.  
> FLAG -> picoCTF{00000715}

# ARMssembly2
Actually did nothing lmao, compiled the ARM code using :-
```
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-as -o chall.o chall_2.S
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-gcc -static -o chall chall.o
```
and then passed with the provided argument `3736234946`.
```
(base) kali@LordSensDomain:~$ qemu-aarch64 ./chall 3736234946
Result: 2618770246
hex(2618770246)
>>> '0x9c174346'
```
The way it works is, We are given the arguement 3736234946 which is stored in [sp+12]. We intialize two counters in [sp+24] and [sp+28] Now the loop starts at L2 Label and continues as logne the increment-1 counter is less than than w0. Inside the loop [sp+24] and [sp+28] are incremented by 3 and 1 respectively. When the loop ends the [sp+24} returns its value which is 3 times the arguement.
> FLAG -> picoCTF{9c174346}

# ARMssembly3
Smooth.
```
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-as -o chall.o chall_3.S
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-gcc -static -o chall chall.o
```
Passed with the provided argument `4012702611`.
```
(base) kali@LordSensDomain:~$ qemu-aarch64 ./chall 4012702611
Result: 63
hex(63)
>>> '0x3f'
```
The way it works is, It starts by initializing the integer in w0 and then enters a loop. Checks if the LSB of the integer is 1 using the and instruction. If the LSB is 1, it calls func2 to add 3 to a result stored in w0. The integer is then right-shifted (lsr) by 1 bit. The loop continues until the integer becomes zero. Finally, the result is printed, showing how many times the LSB was 1 and the corresponding increments.
> FLAG -> picoCTF{0000003f}

# ARMssembly4
Smooth again.
```
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-as -o chall.o chall_4.S
(base) kali@LordSensDomain:~$ aarch64-linux-gnu-gcc -static -o chall chall.o
```
Passed with the provided argument `3434881889`.
```
(base) kali@LordSensDomain:~$ qemu-aarch64 ./chall 3434881889
Result: 3434882004
hex(3434882004)
>>> '0xccbc23d4'
```
The way it works is,  
The input argument 3434881889 is converted to an integer and passed to func1. func1: If the argument is less than or equal to 100, it calls func3. If the argument is greater than 100, it adds 100 to it and calls func2.
func2: If the value is less than or equal to 499, it subtracts 86 and calls func4. If the value is greater than 499, it adds 13 and calls func5.

func5: Calls func8, which adds 2 to the value.

fun6 and fun7 have not been called anywhere.

func1: Finally, the modified value is returned and prints 3434882004.
> FLAG -> picoCTF{ccbc23d4}
