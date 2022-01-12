---
layout: post
title: ctf - exhibit - solution
---
Here is the solution to CTF ['exhibit'](https://hiyaleejohnson.github.io/ctf3). This time with video no less!

<video controls="" width="100%">
  <source  src="https://raw.githubusercontent.com/hiyaleejohnson/hiyaleejohnson.github.io/master/videos/CTF_Exhibit_Solution.mp4" type="video/mp4">
</video>

### 1
Open a browser to start hunting for the flag.  

Note that there isn't much to see on the page.  

Look at the page source to see if anything is disclosed.  

Note that there isn't much to see in the source.  

Return to the page and click on the links.  

Note that path becomes "/index".  

Look at the page source to see if anything new is disclosed.  

Note that again there isn't much to see in the source.  

Enumerate possible paths (based on "/index") such as "/index.php".  

Note that the page has reflected the input back.  

Look at the page source to see if anything new is disclosed.  

Note that again there isn't much to see in the source.  

Enumerate further possible paths (based on "/index") such as "/index.html".  

--*an attacker would not be doing this slowly and manually like this!*   

Check source again and discover API paths are disclosed.  

### 2  
Check disclosed API paths.  

Note that "api/v2/customers" returns a forbidden response.  

Note that "api/v2/users" discloses information (list of userIds).  

Use the format of the disclosed API paths to assume the API path path format for users and enumerate the now known userID values (e.g. "/api/v2/user/3094").  

All paths are returned as "Not Found".  

Change path to "api/v1/<userId>" (e.g. "/api/v1/user/3098") looking for an earlier version of the API.   

Note that more information is disclosed.    

Using the format we now know for the API paths use the newly disclosed customerId information to look for further information.  

Name details now returned - "Farookh Bulsara".  

Look for information using the earlier disclosed hashId (e.g. "api/v1/hash/31").  

Path does not load a page but a different error message is returned; "Method Not Allowed" instead of "Forbidden" or "Not Found".  

Try a different HTTP request medthod such as POST (instead of GET).  

A successful response returns a hashValue that can be saved for later use.  

Save all the information disclosed by the browser.  

--*video shows data for one customer being enumerated but an attacker would be saving all the customer data.*  

### 3  
Next stage is to leave the browser and try to get onto the server using the data disclosed via the browser.  

Port scan to find open ports.  

Port 22 is open so try and SSH connection using the found firstName, lastName and hashValue to guess credentials.  

SSH connection fails and response advises that "this service allows sftp connections only".  

SFTP (SSH File Transfer Protocol) runs over SSH so try and SFTP connection using the same credentials.  

Access is obtained so hunt around for the flag.  

All directories ("[alvinnathaniel](https://en.wikipedia.org/wiki/Xzibit)", "[farookhbulsara](https://en.wikipedia.org/wiki/Freddie_Mercury)", "[harrywebb](https://en.wikipedia.org/wiki/Cliff_Richard)", "[tracymarrow](https://en.wikipedia.org/wiki/Ice-T)") are accessible and seem to contain a "notes.txt" file.  

Grab the files to look at locally.  

Search through the files for the flag (flag format begins '{').  

**We have flag!**  

### Conclusion  
This CTF was a lot less CTF-like than previous ones and focused on security misconfigurations and deviations from best practice:
* Framework Misconfiguration.
* Information Disclosure (via comments, meaningfuly named parameters, meaningful API paths and meaningful error information).
* Multiple versions of APIs remain place.
* Server misconfiguration does not limit HTTP methods.
* Server misconfiguration uses passwords for SFTP instead of key.
* Server misconfiguration of SFTP exposes all users files (flag was found in Tracy Marrow's notes despite using Farookh Bulsara's creds to login).


#### Aside
Disappointingly very few of the CTF players contacted me to be pleased with themselves for spotting that the named users are all the real names of celebrities </shakes head sadly>.  

*And yes, I know I spelled Farrokh wrong! C'est la vie.*
 
### Thank You
Thank you for the music "Cumbia de los Barrios" [El Hijo de la Cumbia](https://freemusicarchive.org/music/El_Hijo_de_la_Cumbia/Freestyle_de_Ritmos/6_Cumbia_De_Los_Barrios).  
[Attribution-NonCommercial-NoDerivs 3.0 United States (CC BY-NC-ND 3.0 US)](https://creativecommons.org/licenses/by-nc-nd/3.0/us/)
 
