### Level 21
Mission : User eloise has saved her password in a particular way. 

Display all visible files in the directory : 

```
ls -l

-rw-r----- 1 root iris 17484 Jul 26 08:54 eloise
-rw-r----- 1 root iris    31 Jul 26 08:53 flagz.txt
-rw-r----- 1 root iris    16 Jul 26 08:54 irispass.txt
-rw-r----- 1 root iris   195 Jul 26 08:53 mission.txt
```

The content of `eloise` seems to be a ciphertext. 

Noticed that the text ends with a `=` that makes the ciphertext to seems like it's b64-encoded.

I decided to export the file to the local machine :

`scp -P 5000 iris@venus.hackmyvm.eu:~/eloise .`

Analyze `eloise` :

`base64 -d eloise > eloise_dec`

```
file eloise_dec

eloise_dec: JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, Exif Standard: [TIFF image data, big-endian, direntries=4], baseline, precision 8, 394x102, components 3
```

It's a JPEG/JPG file, decode it with `.jpg` as the file extension :

`base64 -d eloise > eloise.jpg`

Open the image to obtain the password.

`password : y*************m`

Login as `eloise` with the password obtained :

```
su eloise
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 21`

### Level 22
Mission :User lucia has been creative in saving her password.

Display the content of `hi` :

```
cat hi

00000000: 7576 4d77 4644 5172 5157 504d 6547 500a
```

`7576 4d77 4644 5172 5157 504d 6547 500a` seems to be a hex encoded strings.

Decode the hex encoded strings :

`cat hi | xxd -r -p`

`password : u*************P`

Login as `lucia` with the password obtained :

```
su lucia
password : <password>
```

Display the content of `flagz.txt` to obtain `Flag Level 22`

### Level 23
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 23`

### Level 24
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 24`

### Level 25
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 25`

### Level 26
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 26`

### Level 27
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 27`

### Level 28
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 28`

### Level 29
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 29`

### Level 30
Mission :

Display the content of `flagz.txt` to obtain `Flag Level 30`

Thanks a lot for reading ~
