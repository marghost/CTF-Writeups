# Beginner - Web (by Viper)

## Crawler

* **Track:** web
* **Points:** 3

### Challenge

> What page does a crawler check to see where he can and cannot go?  It is used to instruct bot likes google which page they can or cannot  show on their search engine, it is however a good source of information  to find hidden page without bruteforcing.  Use the server http://beginner-web.hfctf.ca. The answer is a full flag not just the file name.

### Solution

http://beginner-web.hfctf.ca/robots.txt

### Flag

```
HF-27f5e15b6af3223f1176293cd015771d
```

## Find an alternate index

* **Track:** web
* **Points:** 6

### Challenge

> Are you able to find a hidden website under the http://beginner-web.hfctf.ca/?
 It is important to check the other files under a website that you want to pentest.
> Recommended tools: nikto, dirb

### Solution

http://beginner-web.hfctf.ca/index.htm

### Flag

```
HF-DA371569A494D6953447F68C2F6316B2
```

## Port Scan

* **Track:** web
* **Points:** 3

### Challenge

> By default, nmap will only scan the top 1000 ports. Can you learn  how to fix this? If you find a weird port, you can poke it with nc  (netcat).
> The wanted port is within the 13XXX.
> Address: beginner-web.hfctf.ca
> Recommended Tools: nmap, nc (netcat)

### Solution

    nmap -p-

    ┌─[✗]─[user@parrot]─[~/Downloads]
    └──╼ $netcat beginner-web.hfctf.ca 13337
    HF-ed1225fcf8f90eaf704973df7aea7e58

### Flag

```
HF-ed1225fcf8f90eaf704973df7aea7e58
```
