### Level 1
Mission : User sophia has saved her password in a hidden file in this folder. Find it and log in as sophia.

List both visible and hidden files in a directory :
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

Display the content of `flagz.txt` to obtain `Flag Level 1`

### Level 2


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


### Level 3
### Level 4
### Level 5
### Level 6
### Level 7
### Level 8
### Level 9
### Level 10
