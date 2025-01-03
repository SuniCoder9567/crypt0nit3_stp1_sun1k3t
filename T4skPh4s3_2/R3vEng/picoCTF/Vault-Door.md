# vault-door-training
Just a java program that grants access is the flag provided is correct. Here the flag was already given.
```
import java.util.*;

class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
        Scanner scanner = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
   }

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_3808d338b46");
    }
}
```

> FLAG -> w4rm1ng_Up_w1tH_jAv4_3808d338b46

# vault-door-1
The password was again given but we had to `descramble` it based on the way it was given `index` wise.  
```
public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '3' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == 'f' &&
               password.charAt(30) == 'b' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == '6' &&
               password.charAt(26) == 'f' &&
               password.charAt(31) == '0';
    }
}
```
> FLAG -> picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}

# vault-door-3
Just a script I made to math the flag.
```
public class solve_kar {
    public static void main(String[] args) {
        String password = "jU5t_a_sna_3lpm12g94c_u_4_m7ra41";
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        System.out.println(buffer);
    }
}
```
> FLAG -> picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c79a21}

# vault-door-4
A bunch of characters were given which needed to be matched with the flag input. Here is the code that converted em all into ASCII
```
public class translate_kar{
    public static void main(String[] args) {
        int[] decimal = {106, 85, 53, 116, 95, 52, 95, 98};
        int[] hex = {0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f};
        int[] octal = {0142, 0131, 0164, 063, 0163, 0137, 0146, 064};
        char[] ascii = {'a', '8', 'c', 'd', '8', 'f', '7', 'e'};
        
        StringBuilder result = new StringBuilder();
        
        for (int b : decimal) result.append((char)b);
        for (int b : hex) result.append((char)b);
        for (int b : octal) result.append((char)b);
        for (char c : ascii) result.append(c);
        
        System.out.println(result.toString());
    }
}
```

> FLAG -> picoCTF{jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e} 

# vault-door-5
Nothing much, just a base64 decode and hex -> ASCII.  
```
public class URLDecoder {
    public static void main(String[] args) {
        String encoded = "%63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%65%33%31%35%32%62%66%34";
        System.out.println("Decoded: " + urlDecode(encoded));
    }

    public static String urlDecode(String input) {
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < input.length(); i += 3) {
            String hex = input.substring(i + 1, i + 3);
            char c = (char) Integer.parseInt(hex, 16);
            result.append(c);
        }
        return result.toString();
    }

    public static String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i = 0; i < input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }
}
```


> FLAG -> picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4}

# vault-door-6
```
public class XORhaibas {
    public static void main(String[] args) {
        int[] bytes = {
            0x3b, 0x65, 0x21, 0xa, 0x38, 0x0, 0x36, 0x1d,
            0xa, 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa,
            0x21, 0x1d, 0x61, 0x3b, 0xa, 0x2d, 0x65, 0x27,
            0xa, 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36
        };
        
        StringBuilder result = new StringBuilder();
        for (int b : bytes) {
            int xored = b ^ 0x55;
            result.append((char)xored);
        }
        
        System.out.println(result.toString());
    }
}
```

> FLAG -> picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc} 

# vault-door-7
Nothing much again, right shifts move the desired byte into the least significant byte position and a bitwise AND with 0xFF ensures only the least significant byte is kept.
```
public class bitshiftmaujmasti {
    public static void main(String[] args) {
        int[] x = {
            1096770097, 1952395366, 1600270708, 1601398833,
            1716808014, 1734304867, 942695730, 942748212
        };

        byte[] hexBytes = new byte[32]; 
        int index = 0;

        for (int i = 0; i < x.length; i++) {
            hexBytes[index++] = (byte) ((x[i] >> 24) & 0xFF); 
            hexBytes[index++] = (byte) ((x[i] >> 16) & 0xFF); 
            hexBytes[index++] = (byte) ((x[i] >> 8) & 0xFF);  
            hexBytes[index++] = (byte) (x[i] & 0xFF);        
        }

     
        System.out.print("hexBytes: ");
        for (byte b : hexBytes) {
            System.out.printf("%02X ", b); 
        }
        System.out.println();
    }
}
```
> FLAG -> picoCTF{A_b1t_0f_b1t_sh1fTiNg_dc80e28124}

# vault-door-8
Masking and swapping of bits take place here.

```
import java.util.*;

class akhridwaar {
    public static void main(String[] args) {
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4,
            0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86,
            0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xD2,
            0xD0, 0xB4, 0xE1, 0xC1, 0xE0, 0xD0, 0xD0, 0xE0
        };

      
        System.out.println("picoCTF{" + String.valueOf(unscramble(String.valueOf(expected))) + "}");
    }

    static public char[] unscramble(String input) {
       
        char[] a = input.toCharArray();
        
       
        for (int b = 0; b < a.length; b++) {
            char c = a[b];
            c = switchBits(c, 6, 7);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 3, 4);
            c = switchBits(c, 0, 1);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 5, 6);
            c = switchBits(c, 0, 3);
            c = switchBits(c, 1, 2);
            a[b] = c;
        }
        return a;
    }

    static public char switchBits(char c, int p1, int p2) {
 
        char mask1 = (char) (1 << p1);
        char mask2 = (char) (1 << p2);
        char bit1 = (char) (c & mask1);
        char bit2 = (char) (c & mask2);
        char rest = (char) (c & ~(mask1 | mask2));
        char shift = (char) (p2 - p1);
        return (char) ((bit1 << shift) | (bit2 >> shift) | rest);
    }
}
```

> FLAG -> picoCTF{s0m3_m0r3_b1t_sh1fTiNg_91c642112}
