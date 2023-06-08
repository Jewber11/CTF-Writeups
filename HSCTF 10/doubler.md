![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/0357c8c1-b261-49e9-bc57-05b7d43c9120)

This was a fun pwn challenge and the only pwn challenge I solved during the competition. This challenge tasked you with inputting a number so that the program would return -100. At first this seems impossible because you aren't able to input anything negative so you should even be able to get a negative number out. However, I noticed that when you inputted the max integer c could handle: 2147483647, the output of the program was -2 which meant the program treated the max int as -1. Knowing this, I then tested what would happen if I added or subtracted 50 from the max int value. When I did this I got an error if you added 50 to the max int value saying that you can't input negatives, however, if you subtracted 50 from the max int value, the program intepreted the number as -50 like we needed meaning in evaluated to -100 and gave us the flag: 

flag{double_or_nothing_406c561}

Note: I ended up actually subtracting 49 from the max int because when I subtracted 50 from it, I got -102 out so I just subtracted 1 more from the max int and then got the flag. I don't know why I needed to subtract 49 instead of 50 but I guess you do.
