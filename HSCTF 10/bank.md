![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/26396f86-9769-4d7c-9b5d-417ee0df9254)

This challenge tasked you with finding the amount of computers you could hack in a given timeframe when the computers could be hacked. This challenge was particularly hard for me because I have only ever done one competitve programming tournament and so I don't really know many of the algorithms that are used for these types of questions so I had to do some googling to figure out what algorithm I needed to use. After a while, I figured out I needed to use the greedy algorithm(fitting algorithm for the chall) to find the number of account I could compromsie given an input. My implementation of the greedy algorithm was:

```

for _ in range(5):
    num_accounts = int(input())
    accounts = []
    
    for _ in range(num_accounts):
        a, b = map(int, input().split())
        accounts.append([a, b])
    
    accounts.sort(key=lambda x: x[0])
    
    current_end = 0
    hacked = 0
    
    for account in accounts:
        hack_start = max(current_end, account[0])
        hack_end = hack_start + 10
        
        if hack_end <= account[1]:
            hacked += 1
            current_end = hack_end
    
    print(hacked)

```

After running the code on the netcat inputs, I got the flag: flag{gr33dy_4lg0r1thm_048cc38517}
