![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/26134c12-a12d-47fc-aa66-034f94fa80f6)

For this challenge, you were given a nothing.png picture. Since this was in the forensics category, I knew it was a stenography challenge so I did my usual stenography routine. This included using the strings command on the image. When I ran strings -n 6 nothing.png, I noticed two important strings. I saw what looked like a potential password and a string hinting to an embedded file.

strings output that were important:

panda_d02b3ab3 --> potential password

flag.txtUT --> embedded file


Since I knew there was an embedded flag.txt file, I ran binwalk --dd=.*" nothing.png

Once extracted, there was a zip file called 399F. I then tried to unzip the file and it gave me a prompt saying I needed a password to unzip flag.txt. I tried the potential password from above and it worked. All I had to do the was cat flag.txt and I got the flag:

tjctf{the_end_is_not_the_end_4c261b91}

It should be noted I spent like 20 minutes on this challenge because of a formatting error where the flag in flag.txt was flag{the_end_is_not_the_end_4c261b91} which made me thing I had to extract something from the text file or go further to find the actual flag. 
