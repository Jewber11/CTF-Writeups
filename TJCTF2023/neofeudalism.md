![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/f848a2ab-3815-4b07-a944-4c492e2def33)


This challenge was one of my least favorite of the ones I attempted. It seemed very guess to the point where I felt like it was just guess the correct stego tool to get the flag. To start this challenge, like the other stenography challenges, I did the usual strings and binwalk commands, as well as pngchecker and file commands. After none of those showed anything promising, I went on to use websites like https://www.aperisolve.com/ and https://stegonline.georgeom.net/upload to see if there was maybe a hidden picture or flag that was only visible in a certain bitplane or if there was information encoded using LSB. After neither of those website gave me anything of use, I then went opn to try every png stenography tool I knew. finally, I got the flag after running zsteg on the png. 

I ran zsteg -a image.png and finally got the flag:
tjctf{feudalism_still_bad_ea31e43b}
