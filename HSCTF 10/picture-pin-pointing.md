![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/da4dd02c-a2d2-4a23-83e5-e6d55af94972)

I loved this challenge because I love to play geoguessr and this was basically that. You were given 3 photos and you were tasked with finding where each photo was take exactly. To solve this, I used the same strategy on all 3 photos: first, I reverse-searched them using google lens, and then based off of what that outputted, I usually had a city that I could look at and then go from there to find other notable features in the picture.

![one](https://github.com/Jewber11/CTF-Writeups/assets/134816588/7c9203fd-088d-49ea-895b-ebd6578696ac)

For picture 1, After reverse searching the photo, I found the name of the city which was Abakaliki in Nigeria. After that, I looked around in Abakaliki for a circular highway entrance because you can see some fencing in the top irght of the photo that indicates theres four streets that meet in a circle. With that, I was then able to find the junction pretty easily since there was really only one highway that went through the city.

![image](https://github.com/Jewber11/CTF-Writeups/assets/134816588/142c59d4-493f-4822-9e2c-ebd3b2de1846)

I then just looked at street view on each side of the circle and found the exact location of 6.308160465836358, 8.101497922707397 or 6.308, 8.101 rounded.

![two](https://github.com/Jewber11/CTF-Writeups/assets/134816588/1728a40c-6745-4a10-9596-efd469059f30)

For picture 2, I did the same thing as picture 1 and reverse-searched the photo. From that search I figured out it was in iceland. Knowing that, and having been to Iceland, I guessed that the location was Reykjavik Harbour/Port. I then looked around there for a place with water surrounded by 3 sides with land. Doing that in street view found me the boat that was in the picture so I knew I was in the right spot. The exact location was 64.15579065815045, -21.938827402578436 or 64.156, -21.939 rounded. 

![three](https://github.com/Jewber11/CTF-Writeups/assets/134816588/5ed75a6c-13cc-49b3-8342-fc56263b5316)

Picture 3 was the hardest by far and took me almost 30 minutes to solve on its own. Reverse-searching it yielded nothing except Russia, which I knew it wasn't because of the language on the bus. Since you only really got the bus to go off of, I decided to google the bus type and number to try and find where it was. After almost 20 minutes of googling, I finally figured out those busses are used in Buenos Aires, Argentina. I then googled the bus number to find the route it took through Buenos Aires and just started looking along the route. After a while, I finally found where it was. The exact location was -34.65598478351247, -58.371121130854064 or -34.656 -58.371

With that you got the flag: flag{worldwide_traveler}
