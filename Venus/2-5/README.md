### Level 11
Mission : The password of the user lucy is in the line that ends with 0JuAZ (these last 5 characters are not part of her password)

Display all visible files in the directory :

```
ls -l

-rw-r----- 1 root violet 16947 Jul 26 08:54 end
-rw-r----- 1 root violet    31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root violet   327 Jul 26 08:53 mission.txt
```

The file that contains the password is visible, find the strings that matches with the description given :

```
awk '/0JuAZ$/{print}' end

OCmMUjebG53giud0JuAZ
```

`0JuAZ` isn't part of the password.

`password : O*************d`

Login as `lucy` with the password obtained :

```
su lucy
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 11`

### Level 12
Mission : The password of the user elena is between the characters fu and ck 

Display all visible files in the directory :

```
ls -l

-rw-r----- 1 root lucy 12720 Jul 26 08:54 file.yo
-rw-r----- 1 root lucy    31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root lucy   205 Jul 26 08:53 mission.txt
```

Based on the description, the password should be `fu<password>ck`.

The file that contains the password isn't hidden, find the strings that matches with the description :

```
awk '/^fu.*ck$/{print}' file.yo

fu4xZ5lIKYmfPLg9tck
```

`password : 4*************t`

Login as `elena` with the password obtained :

```
su elena
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 12`

### Level 13
Mission : The user alice has her password is in an environment variable. 

Display the environment varibale with `env`.

`password : C*************t`

Login as `alice` with the password obtained :

```
su alice
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 13`

### Level 14
Mission : The admin has left the password of the user anna as a comment in the file passwd. 

Display both visible and hidden files in the directory :

```
ls -la

drwxr-x--- 2 root  alice 4096 Jul 26 08:53 .
drwxr-xr-x 1 root  root  4096 Jul 26 08:53 ..
-rw-r--r-- 1 alice alice  220 Apr 23 21:23 .bash_logout
-rw-r--r-- 1 alice alice 3526 Apr 23 21:23 .bashrc
-rw-r--r-- 1 alice alice  807 Apr 23 21:23 .profile
-rw-r----- 1 root  alice   31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root  alice  231 Jul 26 08:53 mission.txt
```

There's no file named `passwd`.

```
find / -name "passwd" 2>/dev/null

/usr/share/lintian/overrides/passwd
/usr/share/doc/passwd
/usr/bin/passwd
/etc/pam.d/passwd
/etc/passwd
```

I started with the shortest path `/etc/passwd` and search for the password :

```
cat /etc/passwd | awk '/anna/{print}'
anna:x:1015:1015::/pwned/anna:/bin/bash

cat /etc/passwd | awk '/alice/{print}'
alice:x:1014:1014:w*************x:/pwned/alice:/bin/bash
```

`password : w*************x`

Login as `anna` with the password obtained :

```
su anna
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 14`

### Level 15
Mission : Maybe sudo can help you to be natalia.

Tried to have a root authority : 

```
sudo -i

Sorry, user anna is not allowed to execute '/bin/bash' as root on venus.
```

Specify the username that needs root authority and the directory required :

`sudo -u natalia /bin/bash`

Display the content of `flagz.txt` to obtain `Flag Level 15`

### Level 16
Mission : The password of user eva is encoded in the base64.txt file

Display all visible files in the directory :

```
ls -l

-rw-r----- 1 root natalia  25 Jul 26 08:54 base64.txt
-rw-r----- 1 root natalia  31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root natalia 189 Jul 26 08:53 mission.txt
-rw-r----- 1 root natalia  16 Jul 26 08:53 nataliapass.txt
```

The password is decoded in base64, decode it with `base64 -d` :

`cat base64.txt | base64 -d`

`password : u*************O`

Login as `eva` with the password obtained :

```
su eva
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 16`

### Level 17
Mission : The password of the clara user is found in a file modified on May 1, 1968. 

Find files that was modified on the specific time given :

`find / -newermt '1968-05-01'`

There seems to be a lot of files modified on the given time, so try to specify more details :

After serveral trial and errors, the timestamp seems to be somehow rounded.

```
find / -type f ! -newermt "1970-05-02" 2>/dev/null

/proc/947072/task/947072/fdinfo/6
/proc/947072/fdinfo/5
/usr/lib/cmdo
```

The password seems to be contained on `/usr/lib/cmdo`, display the content of `cmdo` :

`cat /usr/lib/cmdo`

`password : 3*************9`

Login as `clara` with the password obtained :

```
su clara
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 17`

### Level 18
Mission : The password of user frida is in the password-protected zip (rockyou.txt can help you) 

There's no existing file named `rockyou.txt`, which means it refers to the rockyou wordlist.

We are given a hint to use a wordlist that means this mission is to brutefoce the password-protected zip.

Use `scp` command to copy a file from a server to our local machine :

`scp -P 5000 clara@venus.hackmyvm.eu:~/protected.zip .`

Get the hash of the zip file :

`zip2john protected.zip > protected_hash.txt`

Crack the password of the zip file :

```
john -w=rockyou.txt

Using default input encoding: UTF-8
Loaded 1 password hash (PKZIP [32/64])
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
pass123          (protected.zip/pwned/clara/protected.txt)     
1g 0:00:00:00 DONE (2023-08-18 23:58) 50.00g/s 819200p/s 819200c/s 819200C/s 123456..christal
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```

`protected.zip password : pass123`

Display the content `protected.txt` :

`cat protected.txt`

`password : E*************i`

Login as `frida` with the password obtained :

```
su frida
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 18`

### Level 19
Display the content of `flagz.txt` to obtain `Flag Level 19`
### Level 20
Display the content of `flagz.txt` to obtain `Flag Level 20`
