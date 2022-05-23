# dns_fping
A Xymon "conn" test with reverse nslookup!

Motivation: 
As I use a lot DNS "CNAME" for the name of my servers, I would like to have the real target of my tests
-> So I created a awk wrapper around fping to activate the -n (the name option, that do a reverse lookup)

This can also be usefull to:
- In a LAN to check that the reverse DNS pointer is set correctly 

Warning: 
- This is set globally to all "conn" test: impact?

Prerequisit:
- fping

Test "fping": it should be working and be in your path: correct it or modify the path in the awk script!

Installation: 
- Copy "dns_fping" into /usr/local/sbin/dns_fping
- Change your "xymonserver.cfg"
--  FPING="/usr/local/sbin/dns_fping"          

That's it!

And just for the info: 
fping is used in Xymon with a list of all targets as argument (I dont k
- fping -Ae www.ubi-network.ch wiki.ubi-network.ch www.raku.org ...

Example:
The first name is the name of my device in the xymon hosts file 
The result start with the IP address, then the reverse DNS name (This is the feature), and the result
- The names here are not the same: It should be it mose cases, but It can be normal (you use CNAME in the xymon hosts file) or not... 

![image](https://user-images.githubusercontent.com/8841264/169885468-89c66d9f-21b9-4be8-b0bb-e758f8210778.png)
