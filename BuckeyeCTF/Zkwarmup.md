![image](https://github.com/user-attachments/assets/9156950e-bf3b-4298-a4b6-bc133d9ff80b)

This was a fun challenge that had to do with the concept of zero-knowledge proofs. A zero-knowledge proof is a cryptography concept that is based on a prover and a verifier. The prover needs to prove something to the verifier without giving away any other information than is necessary. A famous example of this is the where's waldo proof. In this proof, the prover has a page with waldo on it and needs to prove to the verifier that they know where waldo is without giving away information as to where waldo is on the page. The prover does this by taking a big board that is much larger than the page and pokes a small hole in. Through the hole, the prover shows the verifier waldo, but the verifier gets no actual information as to where waldo would be on the page if the big board is removed from the page. The specific proof used in this challenge was the Feige–Fiat–Shamir identification scheme (https://en.wikipedia.org/wiki/Feige%E2%80%93Fiat%E2%80%93Shamir_identification_scheme). In this zero-knowledge proof, the prover has to prove they know the value of $y$ such that $y^2 (mod) n = x * v^b (mod) n$ .

Looking through the source code, we see that the value x is generated based on the current time

![image](https://github.com/user-attachments/assets/764a1f7d-3797-4224-ad78-d11cbfd3a583)

This is a problem because, as the attacker, we can now get the value of x by just running a script on the server that also generates x based on the same time. Once we have x, we can then trick the program into thinking we know the value of the sqrt(y) for both test cases. We start by sending a value s that is then squared mod n.

![image](https://github.com/user-attachments/assets/feee7f84-7f4f-4126-8dce-1590945e115c)

If b = 0, we send the program s * x and then if b = 1, we can just send the program s. 

We have to run this 128 times so I wrote a script using pwntools to do it. I also has a super small brute force for the value of x by just trying 5 seconds before to five seconds after the generated time.time() to make sure I found x every try.
```
from pwn import *
import random
import math

conn = remote('challs.pwnoh.io', 13421)
random.seed(int(time.time()))
t = int(time.time())
conn.recvuntil('Welcome to zkwarmup!\n')

n_line = conn.recvline().decode().strip()
y_line = conn.recvline().decode().strip()

n = int(n_line.split('=')[1].strip())
y = int(y_line.split('=')[1].strip())
for i in range (-10,10):
        random.seed(t+i)
        x = random.randrange(1,n)
        if (x**2) % n == y:
                break
for i in range(128):
        s = random.randrange(1,n)
        payload = (s**2) % n
        conn.sendlineafter("Provide s:", str(payload))

        b_line = conn.recvline().decode().strip()
        b = int(b_line.split('=')[1].strip())

        if b == 0:
                conn.sendlineafter("Provide z:", str(s * x))
        if b == 1:
                conn.sendlineafter("Provide z:", str(s))
        result = conn.recvline()
conn.interactive()
```


Running the script, we get the flag bctf{c4n_s0m30ne_g1v3_m3_a_r3a1_c01n_t0_fl1p}
