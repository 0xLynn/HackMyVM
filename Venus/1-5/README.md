### Level 1
Mission : User sophia has saved her password in a hidden file in this folder. Find it and log in as sophia.

List both visible and hidden files in the directory :
```
ls -la

drwxr-x--- 1 root   hacker 4096 Jul 26 08:55 .
drwxr-xr-x 1 root   root   4096 Jul 26 08:53 ..
-rw-r----- 1 root   hacker   31 Jul 26 08:55 ...
-rw-r--r-- 1 hacker hacker  220 Apr 23 21:23 .bash_logout
-rw-r--r-- 1 hacker hacker 3621 Aug 10 14:17 .bashrc
-rw-r----- 1 root   hacker   16 Jul 26 08:53 .myhiddenpazz
-rw-r--r-- 1 hacker hacker  807 Apr 23 21:23 .profile
-rw-r----- 1 root   hacker  287 Jul 26 08:53 mission.txt
-rw-r----- 1 root   hacker 2542 Jul 26 08:53 readme.txt
```
Display the content of `.myhiddenpazz` :

`cat .myhiddenpazz`

`password : Y*************c`

Login as `sophia` with the password obtained :

```
su sophia
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 1`

### Level 2

Mission : The user angela has saved her password in a file but she does not remember where ... she only remembers that the file was called whereismypazz.txt.

List both visible and hidden files in a directory :

```
ls -la

drwxr-x--- 1 root   sophia 4096 Jul 26 08:53 .
drwxr-xr-x 1 root   root   4096 Jul 26 08:53 ..
-rw-r--r-- 1 sophia sophia  220 Apr 23 21:23 .bash_logout
-rw-r--r-- 1 sophia sophia 3587 Aug 10 14:20 .bashrc
-rw-r--r-- 1 sophia sophia  807 Apr 23 21:23 .profile
-rw-r----- 1 root   sophia   31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root   sophia  359 Jul 26 08:53 mission.txt
```

Seems like there isn't `whereismypazz.txt`.

Let's walk through all files and directories :

```
find / -name "whereismypazz.txt" 2>/dev/null

/usr/share/whereismypazz.txt
```

Display the content of `whereismypazz.txt` :

`/usr/share/whereismypazz.txt`

`password : o*************e`

Login as `angela` with the password obtained :

```
su angela
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 2`

### Level 3

Mission : The password of the user emma is in line 4069 of the file findme.txt

So, I tried to use `awk` :

`awk 'NR==4069{ print; exit }' findme.txt`

`password : f*************O`

Login as `emma` with the password obtained :

```
su emma
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 3`

### Level 4

Mission : User mia has left her password in the file -.

Display all visible files in a directory :

```
ls -l

-rw-r----- 1 root emma  16 Jul 26 08:53 -
-rw-r----- 1 root emma  31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root emma 170 Jul 26 08:53 mission.txt
```

Display the content of `-` : 

`cat ./-`

`password : i*************s`

Login as `mia` with the password obtained :

```
su mia
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 4`

### Level 5
Mission : It seems that the user camila has left her password inside a folder called hereiam.

List both visible and hidden files in the directory :

```
ls -la

drwxr-x--- 2 root mia  4096 Jul 26 08:53 .
drwxr-xr-x 1 root root 4096 Jul 26 08:53 ..
-rw-r--r-- 1 mia  mia   220 Apr 23 21:23 .bash_logout
-rw-r--r-- 1 mia  mia  3526 Apr 23 21:23 .bashrc
-rw-r--r-- 1 mia  mia   807 Apr 23 21:23 .profile
-rw-r----- 1 root mia    31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root mia   244 Jul 26 08:53 mission.txt
```

There seems to be any folder named `hereiam`, so use `find` to search throughout the entire directory :

```
find / -name "hereiam" 2>/dev/null

/opt/hereiam
```

`cd /opt/hereiam`

List both visible and hidden files in the directory :

```
ls -la

drwxr-xr-x 2 root root 4096 Jul 26 08:53 .
drwxr-xr-x 1 root root 4096 Jul 26 08:53 ..
-rw-r--r-- 1 root root   16 Jul 26 08:53 .here
```

Display the content of `.here` : 

`cat .here`

`password : F*************c`

Login as `camila` with the password obtained :

```
su camila
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 5`

### Level 6
Mission : The user luna has left her password in a file inside the muack folder. 

Display all visible files in the directory :

```
ls -l

-rw-r-----   1 root camila    31 Jul 26 08:53 flagz.txt
-rw-r-----   1 root camila   226 Jul 26 08:53 mission.txt
drwxr-xr-x 551 root root   12288 Jul 26 08:54 muack
```

There seems to be a bunch of folders, so I tried to search for existing files :

```
find ./muack -type f

./muack/111/111/muack
```

Display the content of `muack` :

`cat ./muack/111/111/muack`

`password : j*************c`

Login as `luna` with the password obtained :

```
su luna
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 6`

### Level 7
Mission : The user eleanor has left her password in a file that occupies 6969 bytes. 

Use `find` to find files with the description given :

```
find / -size 6969c 2>/dev/null

/usr/share/moon.txt
```

Display the content of `moon.txt` :

`cat /usr/share/moon.txt`

`password : U*************b`

Login as `eleanor` with the password obtained :

```
su eleanor
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 7`

### Level 8
Mission : The user victoria has left her password in a file in which the owner is the user violin.

Use `find` to find files with the description given :

```
find / -user violin 2>/dev/null

/usr/local/games/yo
```

Display the content of `yo` :

`cat /usr/local/games/yo`

`password : p*************j`

Login as `victoria` with the password obtained :

```
su victoria
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 8`

### Level 9
Mission : The user isla has left her password in a zip file.

Use `find` to find files with the description given :

```
find / -name *.zip 2>/dev/null

/pwned/victoria/passw0rd.zip
```
Seems like the zip file we're looking for is located in the current directory.

Display all visible files in the directory :

```
ls -l

-rw-r----- 1 root victoria  31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root victoria 179 Jul 26 08:53 mission.txt
-rw-r----- 1 root victoria 220 Jul 26 08:54 passw0rd.zip
```

Unzip `passw0rd.zip` :

```
unzip passw0rd.zip

Archive:  passw0rd.zip
checkdir error:  cannot create pwned
                 Permission denied
                 unable to process pwned/victoria/passw0rd.txt.
```
Seems like the current directory is a write-protected directory, so try to extract to another directory :

```
unzip passw0rd.zip -d /tmp/venus

Archive:  passw0rd.zip
 extracting: /tmp/venus/pwned/victoria/passw0rd.txt
```

Display the content of `passw0rd.txt` :

`cat /tmp/venus/pwned/victoria/passw0rd.txt`

`password : D*************b`

Login as `isla` with the password obtained :

```
su isla
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 9`

### Level 10
Mission : The password of the user violet is in the line that begins with a9HFX (these 5 characters are not part of her password.). 

Display all visible files in the directory : 

```
ls -l

-rw-r----- 1 root isla    31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root isla   318 Jul 26 08:53 mission.txt
-rw-r----- 1 root isla 16968 Jul 26 08:54 passy
```

Use `awk` to find the password with the description given :

```
awk '/^a9HFX/{print}' passy

a9HFXWKINVzNQLKLDVAc
```

`a9HFX` is not part of the password.

`password : W*************c`

Login as `violet` with the password obtained :

```
su violet
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 10`

Thanks a lot for reading ~
