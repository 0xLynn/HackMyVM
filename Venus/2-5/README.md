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



Display the content of `flagz.txt` to obtain `Flag Level 13`
### Level 14
Display the content of `flagz.txt` to obtain `Flag Level 14`
### Level 15
Display the content of `flagz.txt` to obtain `Flag Level 15`
### Level 16
Display the content of `flagz.txt` to obtain `Flag Level 16`
### Level 17
Display the content of `flagz.txt` to obtain `Flag Level 17`
### Level 18
Display the content of `flagz.txt` to obtain `Flag Level 18`
### Level 19
Display the content of `flagz.txt` to obtain `Flag Level 19`
### Level 20
Display the content of `flagz.txt` to obtain `Flag Level 20`
