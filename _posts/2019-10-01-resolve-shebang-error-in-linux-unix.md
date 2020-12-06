---
layout: post
published: true
title: Resolve shebang error in Linux/Unix
date: '2019-10-01'
tags:
  - shebang
  - troubleshooting
  - dos2unix
  - line ending characters
---
### Situation
When running a script containing `shebang` in a Linux / Unix environment, the following error may occur:

> **Error:** /usr/bin/env: ‘python3\r’: No such file or directory  


```bash
$ cat hello.py
#!/usr/bin/env python3

print("hello world")

$ ./hello.py
/usr/bin/env: ‘python3\r’: No such file or directory
```  


### Cause
This error is caused by **line ending characters**.

If the system where the script is written or modified is a Windows OS platform, line ending character **CR + LF** of the Windows OS is applied to the script. On Linux / Unix OS, the line ending character is **LF**, the script will not be recognized properly.  



### Solution
Simply install a tool called `dos2unix` and convert the OS platform style of the file.  

```bash
$ sudo apt install dos2unix
$ cat hello.py
#!/usr/bin/env python3

print("hello world")

$ ./hello.py
/usr/bin/env: ‘python3\r’: No such file or directory
$ dos2unix hello.py
dos2unix: converting file hello.py to Unix format ...
$ ./hello.py
hello world

$

```
