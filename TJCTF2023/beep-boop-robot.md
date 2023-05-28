![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/6660d631-ab6b-4be2-a0f3-7c4243de9ade)

This was a fun challenge. To start, I started doing all of my usual stenography like strings, binwalk,etc. After that didn't work I looked at the wav file in a spectrogram but there was no hidden image. Eventually, I decided to actually listen to the wav file and the answer became pretty obvious. the wav file contained a recording of morse code. All I did from there was use this website: https://morsecode.world/international/decoder/audio-decoder-adaptive.html to extract the message from the morse code which read: hihowareyoudoing.theflagistjctfthisisallonewordlmao.

So then wrapping the flag you got: tjctf{thisisallonewordlmao}
