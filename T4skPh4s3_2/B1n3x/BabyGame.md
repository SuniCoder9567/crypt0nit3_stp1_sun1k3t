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
