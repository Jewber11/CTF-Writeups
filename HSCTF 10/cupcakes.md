![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/53fa7ed4-516a-425c-9634-0dad5b1e0985)


This was another crpyto challenge where you were given the encrpyted string "avxmsvyusbyxj" and a keyword "SIFT". Since I didn't immediately recognize this cipher, I used a cipher identifier found here: https://www.boxentriq.com/code-breaking/cipher-identifier The two ciphers that were the highest likelyhood of being the cipher used to encrpyt the message were the bifid and vigenere ciphers. Knowing that, I just tried to decode the cipher text using both methods and it turns out the ciphertext was encoded using a vigenere cipher. Once I decoded the message, it became: "instantbatter" meaning the flag was:

flag: flag{instantbatter}
