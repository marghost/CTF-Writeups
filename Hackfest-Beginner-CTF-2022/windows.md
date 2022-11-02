# Beginner - Windows (by Viper and h3xit)

## 01 - New Employees ( Start Here )  

* **Track:** windows
* **Points:** 2

### Challenge

> Welcome new employee!
> Here is your openvpn package to access the internal network,
> Please ensure you read and understand the code of conduct and the documentation for new employees.
> The documentation is located at http://10.10.0.71/welcome_template.html
> In the mean time you should receive your account name in the following month of your hiring.
> Happy Reading!

### Solution

    ┌─[✗]─[user@parrot]─[~/Downloads]
    └──╼ $sudo openvpn --config ./client_config.ovpn

go to http://10.10.0.71/welcome_template.html

Hi {{ first_name }} {{ last_name }}

Welcome to Acme Inc.

This is a message from your IT department. To login to our system,  you must use the default password : "Soleil123" then change to a  stronger one.

Your username is {{ first_name[0] }}{{ last_name }}

Have a good one !
HF-1d47a8c842d68d311a6eccf5dd9de018

### Flag

```
HF-1d47a8c842d68d311a6eccf5dd9de018
```

## 02 - Domo Arigato.. 

* **Track:** windows
* **Points:** 5

### Challenge

> Mr Roboto

### Solution

robot.txt
HF-60673a35e66dcc3ff74068d794821070

### Flag

```
HF-60673a35e66dcc3ff74068d794821070
```

## 03 - Welcome Password 

* **Track:** windows
* **Points:** 5

### Challenge

> What is the company welcome password?
> You should be able to compromise some users with this welcome  password, more often than not people are to lazy to change that  password.
> A good source of inspiration is this wordlist: https://github.com/insidetrust/statistically-likely-usernames
> Recommended tool: kerbrute
> Are you able to obtain some more privilege with the use of that password?

### Solution

Found on the first flag webpage.

### Flag

```
Soleil123
```
