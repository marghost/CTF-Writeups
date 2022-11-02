# Beginner - Steganography (by Dax)

## 1 - Encrypted

* **Track:** steganography
* **Points:** 5

### Challenge

> This simple file contains 3 flags. Can you dig deep enough?
> 01100001 01010110 01100101 01110010 01111001 01010011 01110100  01110010 01101111 01101110 01100111 01010000 01100001 01110011 01110011  01110000 01101000 01110010 01100001 01110011 01100101

### Solution

binary to text = aVeryStrongPassphrase  

    ┌─[user@parrot]─[~/Downloads]
    └──╼ $gpg -d FILE.zip.gpg > File.zip
    gpg: AES.CFB encrypted data
    gpg: encrypted with 1 passphrase

    flag.txt : You found a flag! <ykhti36b2thircqwr31sm17x7wpxsj4b>

### Flag

```
ykhti36b2thircqwr31sm17x7wpxsj4b>
```

## 2 - An Image is Worth a Thousand Words

* **Track:** steganography
* **Points:** 5

### Challenge

> This simple file contains 3 flags. Can you dig deep enough?
> (Use file found during Flag #1)

### Solution

base64 inside flag.jpg = wellPlayed

Steganographic Decoder : https://futureboy.us/stegano/decinput.html
Input img and password  

      PK
    �����…±xI>œTä���ä�����FLAG.mp3UT	�
    ¬7X¬7Xux�è��è��ý7zXZ��æÖ´F�!���t/å£à'ÿ�¡]�#&A]÷ÉóÌðühfmT©þ®ú7_’²a¸§ÚdËŠ_xº­At4jD2G$øÜÀ±’a`ƒ,¤=¶fµ_ÏCúðgØÀIìv=}°’žÈ&MŒ¡í&odw£Ò£yHŠ°ÛìS6ÅÄ0dÏ4g[cZÒ‚[ïÒ¿;å¥–E„â%eÖ«å-Ý\ªÿ=žáy:ör;^œiì²5¸’ï)3,�����$Ç7ìµ@‡�½€P��Me„Ù±Ägû����YZPK
    �����;²xI©‹T&5���5�����FLAG.txtUT	�a­7Xb­7Xux�è��è��You found a flag! <b05kruwi3bwczluxupgewpacy2liglfe>
    PK
    �����…±xI>œTä���ä�������������´����FLAG.mp3UT�
    ¬7Xux�è��è��PK
    �����;²xI©‹T&5���5������������´&��FLAG.txtUT�a­7Xux�è��è��PK������œ�������

    flag.txt : You found a flag! <b05kruwi3bwczluxupgewpacy2liglfe>

### Tool

* https://futureboy.us/stegano/decinput.html

### Flag

```
b05kruwi3bwczluxupgewpacy2liglfe
```

## 3 - Things Aren't Always What They Seem

* **Track:** stenography
* **Points:** 5

### Challenge

> This simple file contains 3 flags. Can you dig deep enough?
> (Use file found during Flag #2)

### Solution

    ┌─[✗]─[user@parrot]─[~/Downloads]
    └──╼ $steghide extract -sf FILE.jpg 
    Enter passphrase: 
    wrote extracted data to "FLAG.zip".

    ┌─[✗]─[user@parrot]─[~/Downloads]
    └──╼ $strings FLAG.mp3
    7zXZ
    hfmT
    At4jD2G$
    &odw
    4g[c
    ┌─[user@parrot]─[~/Downloads]
    └──╼ $binwalk FLAG.mp3

    DECIMAL       HEXADECIMAL     DESCRIPTION
    --------------------------------------------------------------------------------
    0             0x0             xz compressed data

    ┌─[user@parrot]─[~/Downloads]
    └──╼ $file FLAG.mp3
    FLAG.mp3: XZ compressed data
    ┌─[user@parrot]─[~/Downloads]
    └──╼ $tar -xf FLAG.mp3
    ┌─[user@parrot]─[~/Downloads]
    └──╼ $cat FLAG.txt
    You found a flag! <w11wn5ar7ot0av4k83g768rxscv4kngl>

### Flag

```
w11wn5ar7ot0av4k83g768rxscv4kngl
```
 