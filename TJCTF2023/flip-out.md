![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/16ac95cb-8fe6-464a-9837-b87bde964bd0)

For this challenge you were given a binary that had to do with an app that you connected to. When trying different inputs, I noticed that every number I entered gave a return of "nothing to see here..." This made me think it was a challenge where, if you input the right number, it would print the flag. To test this theory I wrote a simple python script using pwntools to just try every number as an input and then printed the output of the program each time. I originally just did this to see if I was on the right track but ended up getting the flag out. This was definately an unintentional solve but hey, I'll take it.

After running my script from 0-150, I got the flag when the input was 128. The flag was:
tjctf{chop-c4st-7bndbji}
