# ARMAssembly 0
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
