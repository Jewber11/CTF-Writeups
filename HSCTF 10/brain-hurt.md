![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/4f6ae026-bfa7-4d5f-9353-9adb88e22827)

This challenge was another essentially another crypto challenge because it was an implementation of the caesar cipher on ascii characters. The giveaway for this was this encoding code:

encoded_char = chr((ord(c) ^ 0xFF) % 95 + 32)

this Immediately screamed caesar cipher because of how the characters were being shifted because 95+32 is 127(note this doesn't equal 128 bc the mapping index for the characters to their shifted characters starts at 0 and goes 0-127) and there are 128 ascii characters so I knew that the characters were just being shifted like a caesar cipher. Knowing that it was a caesar cipher, I then just wrote a brute-force script to test every shift until the inputted letter because the shifted letter in string: 'ZT_YE\\0|akaY.LaLx0,aQR{"C' which was given in the code as the expected_flag variable.

here is my brute-force script:

