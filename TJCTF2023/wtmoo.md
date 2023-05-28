First off, it should be noted that I didn't solve this challenge within the competition timeframe, but I'm still doing a writeup because I mistyped one character in my flag which is why I never solved it. After seeing that my original flag didn't work I put this challenge on the backburner and kinda forgot about it until the CTF was over. 

To solve the actual challenge, first I decompiled the given binary in ghidra. When looking at the main function, I saw that all the program was do was applying some sort of shift/cipher on your input and then checking to see if it matched up with a string in a strcmp function. 

Here's the decompiled binary in ghidra:

![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/3a850c2c-3829-4914-8e08-d187cce8dd7b)


After looking at the binary, I also noticed that the binary would output the transformed version of the input string unless it was the correct flag. Knowing this, I decided to create essentailly a cipher map so I figure out what each input character became once it was tranformed. To do this, I just inputted abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890 into the program. The output was:
%&'()*+,-./0123456789:;<=>abcdefghijklmnopqrstuvwxyz\]^_ !"#$[

With that, we could just reconstruct the strcmp string and we got the flag as:

tjctf{wtMoo0O0o0o0a7e8f1}

Note: I mistyped here and accidentally entered tjctf{wtMoo0O0o0o0a17e8f1} because I forgot to remove the backslash which became a 1 after the transformation so that's why I never solved the challenge in time :(
