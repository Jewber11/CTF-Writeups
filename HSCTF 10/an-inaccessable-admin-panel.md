<img width="303" alt="image" src="https://github.com/Jewber11/CTF-Writeups/assets/134816588/5d8ec21d-3f0c-47cf-8ec4-77e28d66d240">

This was a fun web challenge where you had to brute-force/reverse engineer a password checking function. If you inspected the source code of the website, there was a file called login.js which had this code:

```
window.onload = function() {
    var loginForm = document.getElementById("loginForm");
    loginForm.addEventListener("submit", function(event) {
        event.preventDefault(); 
    
        var username = document.getElementById("username").value;
        var password = document.getElementById("password").value;
    
        function fii(num){
            return num / 2 + fee(num);
        }
        function fee(num){
            return foo(num * 5, square(num));
        }
        function foo(x, y){
            return x*x + y*y + 2*x*y;
        }
        function square(num){
            return num * num;
        }

        var key = [32421672.5, 160022555, 197009354, 184036413, 165791431.5, 110250050, 203747134.5, 106007665.5, 114618486.5, 1401872, 20702532.5, 1401872, 37896374, 133402552.5, 197009354, 197009354, 148937670, 114618486.5, 1401872, 20702532.5, 160022555, 97891284.5, 184036413, 106007665.5, 128504948, 232440576.5, 4648358, 1401872, 58522542.5, 171714872, 190440057.5, 114618486.5, 197009354, 1401872, 55890618, 128504948, 114618486.5, 1401872, 26071270.5, 190440057.5, 197009354, 97891284.5, 101888885, 148937670, 133402552.5, 190440057.5, 128504948, 114618486.5, 110250050, 1401872, 44036535.5, 184036413, 110250050, 114618486.5, 184036413, 4648358, 1401872, 20702532.5, 160022555, 110250050, 1401872, 26071270.5, 210656255, 114618486.5, 184036413, 232440576.5, 197009354, 128504948, 133402552.5, 160022555, 123743427.5, 1401872, 21958629, 114618486.5, 106007665.5, 165791431.5, 154405530.5, 114618486.5, 190440057.5, 1401872, 23271009.5, 128504948, 97891284.5, 165791431.5, 190440057.5, 1572532.5, 1572532.5];

        function validatePassword(password){
            var encryption = password.split('').map(function(char) {
                return char.charCodeAt(0);
            });
            var checker = [];
            for (var i = 0; i < encryption.length; i++) {
                var a = encryption[i];
                var b = fii(a);
                checker.push(b);
            }
            console.log(checker);
            
            if (key.length !== checker.length) {
                return false;
            }
            
            for (var i = 0; i < key.length; i++) {
                if (key[i] !== checker[i]) {
                    return false;
                }
            }
            return true;
        }


        if (username === "Admin" && validatePassword(password)) {
            alert("Login successful. Redirecting to admin panel...");
            window.location.href = "admin_panel.html";
        }
        else if (username === "default" && password === "password123") {
            var websiteNames = ["Google", "YouTube", "Minecraft", "Discord", "Twitter"];
            var websiteURLs = ["https://www.google.com", "https://www.youtube.com", "https://www.minecraft.net", "https://www.discord.com", "https://www.twitter.com"];
            var randomNum = Math.floor(Math.random() * websiteNames.length);
            alert("Login successful. Redirecting to " + websiteNames[randomNum] + "...");
            window.location.href = websiteURLs[randomNum];
        } else {
            alert("Invalid credentials. Please try again.");
        }
    });
  };
  ```
  
  With this, it became clear that you had to use the values in the key array to reconstruct what password is used to login with the Admin username. To do this, I wrote a python script to figure out what password was encrpyted to become the key array. All the javascript was doing was really just applying the fii function on each character of the password as seen here:

```
var a = encryption[i];
var b = fii(a);
checker.push(b);
```

my script was:

```
target_key = [
    32421672.5, 160022555, 197009354, 184036413, 165791431.5, 110250050,
    203747134.5, 106007665.5, 114618486.5, 1401872, 20702532.5, 1401872,
    37896374, 133402552.5, 197009354, 197009354, 148937670, 114618486.5,
    1401872, 20702532.5, 160022555, 97891284.5, 184036413, 106007665.5,
    128504948, 232440576.5, 4648358, 1401872, 58522542.5, 171714872,
    190440057.5, 114618486.5, 197009354, 1401872, 55890618, 128504948,
    114618486.5, 1401872, 26071270.5, 190440057.5, 197009354, 97891284.5,
    101888885, 148937670, 133402552.5, 190440057.5, 128504948, 114618486.5,
    110250050, 1401872, 44036535.5, 184036413, 110250050, 114618486.5,
    184036413, 4648358, 1401872, 20702532.5, 160022555, 110250050, 1401872,
    26071270.5, 210656255, 114618486.5, 184036413, 232440576.5, 197009354,
    128504948, 133402552.5, 160022555, 123743427.5, 1401872, 21958629,
    114618486.5, 106007665.5, 165791431.5, 154405530.5, 114618486.5,
    190440057.5, 1401872, 23271009.5, 128504948, 97891284.5, 165791431.5,
    190440057.5, 1572532.5, 1572532.5
]

def fii(num):
    return num / 2 + fee(num)

def fee(num):
    return foo(num * 5, square(num))

def foo(x, y):
    return x * x + y * y + 2 * x * y

def square(num):
    return num * num

input_string = ""

for target in target_key:
    char_code = 0

    while True:
        output = fii(char_code)

        if abs(output - target) < 0.001:
            input_string += chr(char_code)
            break

        char_code += 1

print(input_string)
```

running this gave you the string: "Introduce A Little Anarchy, Upset The Established Order, And Everything Becomes Chaos!!"

with that string, I tried to login to the website with username Admin and password as the string above.I was then greeted with this message 
"Remember flag format is flag{} The flag is [username] + ", " + [password] For example, if the username was Username and the password was Password, the flag would be flag{Username, Password}"

with that I got the flag:

flag: flag{Admin, Introduce A Little Anarchy, Upset The Established Order, And Everything Becomes Chaos!!}
                
