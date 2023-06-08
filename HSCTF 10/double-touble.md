![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/8933ce8f-e5a0-4aa0-86e0-0d192051b505)

This challenge gave you a pdf with a hint and then a ciphertext. The hint was "___________ Salad: a green salad of romaine lettuce and croutons dressed with lemon juice, olive oil,
egg, Worcestershire sauce, anchovies, garlic, Dijon mustard, Parmesan cheese, and black pepper. In its
original form, this salad was prepared and served tableside."

this immediately gave away the challenge because it was a caesar cipher. Knowing that, all you had to do was through the cipher text into a decoder like the one at: https://www.dcode.fr/caesar-cipher and you got this out:

"	This should not be too hard.
In fact, I will give it to you right now!
The flag is the following:
AycqypAgnfcpqYpcAmmj
However, it is encoded so you have to decode it first!
Bwahahahaha
Remember, the flag format is flag{}"


to then decode the flag, I remembered that the name of the challenge was double-trouble so I figured the flag was also encrpyted using a caesar cipher so I just ran the flag back through and got out:
CaesarCiphersAreCool 

flag: flag{CaesarCiphersAreCool}
