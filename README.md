# dns_fping
A wrapper for Xymon for a "conn" test with nslookup!

Motivation: 

As I use DNS CNAME a lot, I would like to have the DNS resolution to know the real target of my tests
So I created a awk wrapper around fping

Prerequisit:
- fping

Test "fping": it should be working and be your path: correct it or modify the path in the awk script!

Installation: 
- Copy "dns_fping" into /usr/local/sbin/dns_fping
- Change your "xymonserver.cfg"
--  FPING="/usr/local/sbin/dns_fping"          

That's it!
