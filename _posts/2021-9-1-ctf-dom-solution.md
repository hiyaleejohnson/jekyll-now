---
layout: post
title: ctf - dom - solution
---
Here is the solution to CTF ['dom'](https://hiyaleejohnson.github.io/ctf1) (which has the honour of having to be solved by me just like everyone else, as all the notes taken during creation were misplaced).  

![dom screenshot](/images/dom_screenshot_1.JPG)  

Door photo by [Jack Sharp](https://unsplash.com/@jacksharp_photography) on [Unsplash](https://unsplash.com)  

### 1
View source and observe the very few resources available. 
  
![Page source screenshot](/images/domsolution/ctfdom_viewsource.jpg)

### 2
Download image.
  
![Curl screenshot](/images/domsolution/ctfdom_downloadimage.jpg)

## 3
Open image using archive utility.
  
![Launching archive utility screenshot](/images/domsolution/ctfdom_open7zipfm.jpg)


## 4
Observe new location.txt file and open.  

![Archive utility screenshot](/images/domsolution/ctfdom_openwith7zipusingpassword.jpg)

This required a password, which was a decoded base64 string that had attention drawn to it in the console.  

![Dev console screenshot](/images/domsolution/ctfdom_consoledrawattention.jpg)

Decoded string 'usethisaspassword'.  

![Decoded base64 string screenshot](/images/domsolution/ctfdom_base64valuedecoded.jpg)

File contents revealed.  
  
![Encoded long base64 string screenshot](/images/domsolution/ctfdom_base64locationstring.jpg)  

    <!--Ly8gUGF1bCBTaGFuZSBwZXJmb3JtaW5nICdZb3UndmUgTG9zdCB0aGF0IExvdmluZyBGZWVsaW5nJyAoMTk5Nik= aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1HUFMwcjNSTWVuYw== Ly8gTG9zdCA1IFNlYXNvbnMgaW4gOCBtaW51dGVz aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1HZFQ4ZXFNTzRxaw== Ly8gRXZlcnl0aGluZyBCdXQgVGhlIEdpcmwgLSBNaXNzaW5nIC0gKFRvZGQgVGVycnkgUmVtaXgpIChPZmZpY2lhbCBNdXNpYyBWaWRlbyk= aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1JQWtZNW0wMHJwWQ== Ly8gVGhlIEJsYWNrIEV5ZWQgUGVhcyAtIFdoZXJlIElzIFRoZSBMb3ZlPyAoT2ZmaWNpYWwgTXVzaWMgVmlkZW8p aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj1XcFllZWtRa0FkYw== Ly8gUlVOIERNQywgSmFzb24gTmV2aW5zIC0gSXQncyBMaWtlIFRoYXQgKFZpZGVvKQ== aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj00Ql9VWVlQYi1Haw== Ly8gSW5pIEthbW96ZSAtIEhlcmUgQ29tZXMgVGhlIEhvdHN0ZXBwZXIgKFJlbWl4KSAoVmlkZW8p aHR0cHM6Ly93d3cueW91dHViZS5jb20vd2F0Y2g/dj0xNVVmZk44ZWlsSUx5OGdURzl6ZENBMUlGTmxZWE52Ym5NZ2FXNGdPQ0J0YVc1MWRHVno= Ly9odHRwczovL3d3dy5nb29nbGUuY29tL21hcHMvQDU0LjU0NTY3MjgsLTEuOTM4NzcxMSw1MzY0bS9kYXRhPSEzbTIhMWUzITRiMSE0bTUhM200ITFzMHg0ODdjMjM1Zjk5NGQ4MjMxOjB4YTBlMjM1YTJhYTY2NDM4MiE4bTIhM2Q1NC41NDUyODQhNGQtMS45MjM3NDE=-->

### 5
Decode Base64 string.
  
![Decoded base64 strings screenshot](/images/domsolution/ctfdom_base64locationstringdecoded.jpg)

    <!--// Paul Shane performing 'You've Lost that Loving Feeling' (1996) https://www.youtube.com/watch?v=GPS0r3RMenc // Lost 5 Seasons in 8 minutes https://www.youtube.com/watch?v=GdT8eqMO4qk // Everything But The Girl - Missing - (Todd Terry Remix) (Official Music Video) https://www.youtube.com/watch?v=IAkY5m00rpY // The Black Eyed Peas - Where Is The Love? (Official Music Video) https://www.youtube.com/watch?v=WpYeekQkAdc // RUN DMC, Jason Nevins - It's Like That (Video) https://www.youtube.com/watch?v=4B_UYYPb-Gk // Ini Kamoze - Here Comes The Hotstepper (Remix) (Video) https://www.youtube.com/watch?v=15UffN8eilILy8gTG9zdCA1IFNlYXNvbnMgaW4gOCBtaW51dGVz //https://www.google.com/maps/@54.5456728,-1.9387711,5364m/data=!3m2!1e3!4b1!4m5!3m4!1s0x487c235f994d8231:0xa0e235a2aa664382!8m2!3d54.545284!4d-1.923741-->
  
[![Youtube screenshot of Lost 5 seasons in 8 minutes](/images/domsolution/ctfdom_youtubelost.jpg)](https://www.youtube.com/watch?v=AyOqGRjVtls)    

### 6
Location revealed!  
**Barnard Castle**  

_This may have been written at peak 'Dominic Cummings goes to Barnard Castle'._
  
![Web browser Google Maps screenshot](/images/domsolution/ctfdom_locationrevealed.jpg)  

### 7
**Solution - the distance required.**  
The distance from Rhyl to Barnard Castle via the M6 is 169 miles.
    
![Web browser Google Maps screenshot showing distance of route to final destination](/images/domsolution/ctfdom_distance.jpg)  


### Conclusion  
There was a lot of Base64 in here and it was very CTF-like, but it was thrown together quickly to capitalise on a news event so I make no apologies.  

