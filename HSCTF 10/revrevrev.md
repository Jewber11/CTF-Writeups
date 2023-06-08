![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/da04476d-62d6-4cdb-9ec8-45252964b67c)

This was a super fun and also frustrating challenge for me. In this challenge, you were given some code to a car game and you had to figure out what input string would move your car to a certain spot. At first, I was super confused and got pretty frusterated with this challenge when I tried to solve it legitly because i was trying to figure out a formula or something to describe the car's movement and tried to figure out how different combinations of the moves: 'R', 'r', or 'L' effected each other and the position of the car. After a while, I kinda gave up and wrote a script to brute-force all of the different string combinations. This shouldn't have worked because there were billions of possible string but I got super lucky and the intended string happened to be one of the first combinations tried by the algorithm and it worked. 

Here's the brute-force script:

```
import itertools
def test_permutations():
    chars = ['r', 'L', 'R']
    for perm in itertools.product(chars, repeat=20):
        ins = "".join(perm)
        s = 0
        a = 0
        x = 0
        y = 0
        for c in ins:
            if c == 'r':  # rev
                s += 1
            elif c == 'L':  # left
                a = (a + 1) % 4
            elif c == 'R':  # right
                a = (a + 3) % 4
            else:
                print("This character is not necessary for the solution.")
            if a == 0:
                x += s
            elif a == 1:
                y += s
            elif a == 2:
                x -= s
            elif a == 3:
                y -= s
        if x == 168 and y == 32:
            print("Flag: flag{" + ins + "}")
            return

test_permutations()

```

using this I got that the correct input was rrrrrrrrrrrrrrrrLRLR so the flag was: flag{rrrrrrrrrrrrrrrrLRLR}
