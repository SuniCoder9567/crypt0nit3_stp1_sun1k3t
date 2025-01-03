# babygame01

Just a game huh? Well obviously there is some bs hiding behind it to make it a Binex chal. I used _Ghidra_ to reverse engineer the `game` file.

After disassembling the game file, I was looking into the main function and found this....
```
puts("You win!");
if (local_aa4 != '\0') {
  puts("flage");
  win();
  fflush(stdout);
}
```
There was another function `move_player()` which contained like two more keybinds except the usual `w,a,s,d` provided in the UI. `l` which lets us set the player tile and `p` which solves the game and gives us the flag.
```
  if (param_2 == 'l') {
    iVar1 = getchar();
    player_tile = (undefined)iVar1;
  }
  if (param_2 == 'p') {
    solve_round(param_3,param_1);
  }
  *(undefined *)(*param_1 * 0x5a + param_3 + param_1[1]) = 0x2e;
  if (param_2 == 'w') {
    *param_1 = *param_1 + -1;
  }
  else if (param_2 == 's') {
    *param_1 = *param_1 + 1;
  }
  else if (param_2 == 'a') {
    param_1[1] = param_1[1] + -1;
  }
  else if (param_2 == 'd') {
    param_1[1] = param_1[1] + 1;
  }
  *(undefined *)(*param_1 * 0x5a + param_3 + param_1[1]) = player_tile;
  return;
```
Taking a careful look into the code, there seems to be no `Out of Bounds` checking in the `move_player()` function.  
Now, coming back to the `main` function, analyzing it suggests that the value of `local_aa4` must be `NOT NULL` in order to win the challenge. Currently it is `NULL`. To make it `NOT NULL`, we need to change the position of the player to `(0,-4)`, as `local_aa4` precedes `local_aa0` in the array as per the `init_player()` function. Bringing it to that position, underflows the array and is going to point to `local_aa4` and put the value of `player_title` into it thus making it `NOT NULL`. Affter that, we type in `p` and voila, we get our flag!

> FLAG -> picoCTF{gamer_m0d3_enabled_8985ce0e}

# babygame02
We can deconstruct the game using Ghidra. In this case, our goal is to overwrite the return address on the stack with the address of the win() function in order to retrieve the flag. Initially, a new base pointer (EBP) is set to point to the previous one, and then EBX and ECX are pushed onto the stack. The stack pointer is then decremented by 2720 bytes. During the move_player function, the map, located at -2709 bytes, is pushed onto the stack. Afterward, EAX and a local variable aa8 are pushed, followed by the return address. This creates a 39-byte stack underflow that allows the win() function to be called.
```
        0804967e 55              PUSH       EBP
        0804967f 89 e5           MOV        EBP,ESP
        08049681 53              PUSH       EBX
        08049682 51              PUSH       ECX
        08049683 81 ec a0        SUB        ESP,0xaa0
                 0a 00 00
```

We can't move iteratively one step at a time because doing so would overwrite the previous parameters used in the move_player() function. Therefore, the solution involves moving to y = -1 and then stepping back 39 bytes. The goal is for the last byte of the target address to match the return address of the win() function, which has a least significant byte (LSB) value of 0x70 (the hex value for p). By using the lp command, we can set the player’s position value to p, effectively allowing us to overwrite the return address and trigger the win() function.

> FLAG -> picoCTF{gamer_jump1ng_4r0unD_18d53688}

