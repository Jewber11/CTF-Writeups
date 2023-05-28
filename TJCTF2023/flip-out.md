![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/16ac95cb-8fe6-464a-9837-b87bde964bd0)

For this challenge you were given a binary that had to do with an app that you connected to. When trying different inputs, I noticed that every number I entered gave a return of "nothing to see here..." This made me think it was a challenge where, if you input the right number, it would print the flag. To test this theory I wrote a simple python script using pwntools to just try every number as an input and then printed the output of the program each time. I originally just did this to see if I was on the right track but ended up getting the flag out. This was definately an unintentional solve but hey, I'll take it. I ran my script from 0 to 128 because, when looking at the binary, we see that uVar1 had to be less than 0x81 which is 129 in decimal.

After running the script to brute force every number from 0-128, I got the flag:
tjctf{chop-c4st-7bndbji}

Note: I'm not releasing the script because looking back I probably shouldn't have brute forced it because it probably hurt the infrastructure of the challenge by opening and closing 129 connections in rapid succession. 
