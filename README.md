# dns_fping
A Xymon "conn" test with reverse nslookup!

Motivation: 
- As I use a lot DNS "CNAME" for the name of my servers, I would like to have the real target of my tests

This is usefull to:
- In a LAN, to check if the reverse DNS pointer is set correctly
- If you use CNAME, this will show normally the "final" target hostname (but remember that this hostname is obtained by a reverse lookup query, it shows you nothing more if the PTR record is not set) 

Warning: 
- As this is set globally to all "conn" test: this could have a performance impact! 

Prerequisit:
- fping (test the path: which fping)

Debian: apt-get install fping

Test "fping": it should be working and be in your path: correct it or modify the path in the awk script!

Installation: 
- Copy "dns_fping" into /usr/local/sbin/dns_fping
- Make it executable: chmod +x /usr/local/sbin/dns_fping
- Change your "xymonserver.cfg"
  - FPING="/usr/local/sbin/dns_fping"
  - FPINGOPTS=""         

That's it!

Example:
- The first name is the name of my device in the Xymon hosts file 
- The result 
  - Start with the **color** of the test, then the **IP address** 
  - Then **the reverse DNS name: THE FEATURE of "dns_fping" !!**
  - And finally, **the result of the test**
- As we can see, the names here are not the same! 

![image](https://user-images.githubusercontent.com/8841264/169885468-89c66d9f-21b9-4be8-b0bb-e758f8210778.png)

And just for the info: 
- Xymon send to the ping command a list of all ips (only ips, even for 0.0.0.0 entries) via stdin
- the ping seems not to be used for dns resolution (done before)
- echo "www.ubi-network.ch" | dns_fping 
