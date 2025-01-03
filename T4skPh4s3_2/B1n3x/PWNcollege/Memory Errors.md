# LEVEL 1.0
Nothing, just a simple `buffer overflow` challenge.  
We gotta change the value of the `win` variable.  

I set the payload size to a large one such as `1000` bytes and sent in random long ass stream of aaaaaaaaaaaaaaaaaaaaaaa's.  
The a's r gonna move through and reach the address of `win` and change it's value.
```
The program's memory status:
- the input buffer starts at 0x7ffd090d7880
- the saved frame pointer (of main) is at 0x7ffd090d78f0
- the saved return address (previously to main) is at 0x7ffd090d78f8
- the saved return address is now pointing to 0x582546cb421b.
- the canary is stored at 0x7ffd090d78e8.
- the canary value is now 0x6161616161616161.
- the address of the win variable is 0x7ffd090d78d8.
- the value of the win variable is 0x61616161.

You win! Here is your flag:
pwn.college{YM2F3mBPgaEPQORm98MX-zV4Rif.0VO4IDL3AjN1czW}


Goodbye!
```

> FLAG -> pwn.college{YM2F3mBPgaEPQORm98MX-zV4Rif.0VO4IDL3AjN1czW}

# LEVEL 1.1
Same as the previuos one.
> FLAG -> pwn.college{cqi7_S4fefR8xZ9_BvpyBMo5yez.0FM5IDL3AjN1czW}
