![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/05debb40-e61d-4d02-b8ed-760dc553cd1d)

This challenge was a mongoDB sql injection challenge. To solve it, I just looked up "mongoDB sql injection" and found this website: https://nullsweep.com/a-nosql-injection-primer-with-mongo/ which explained some basic NoSQL injections, one of which was using the string: ' || 'a'=='a to bypass login. Sure enough, I entered that string as both username and password and got the flag.

flag: flag{easier_than_picture_lab_at_least}
