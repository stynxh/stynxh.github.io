---
layout: post
published: false
title: Linux/Unix 환경에서 shebang 오류 해결
---
### 현상

Linux/Unix 환경에서 `shebang` 이 포함되어있는 스크립트를 실행할 때, 다음과 같은 오류가 나는 경우가 있다.

```bash
$cat hello.py
#!/usr/bin/env python3

print("hello world")

$./hello.py
/usr/bin/env: ‘python3\r’: No such file or directory
```

{: .box-error}
**Error:** /usr/bin/env: ‘python3\r’: No such file or directory



### 원인

이 오류는 **line ending characters (줄바꿈 문자)** 때문에 생기는 문제이다.

해당 스크립트를 작성하거나 수정한 시스템이 Windows OS 플랫폼일 경우, Windows OS 의 줄바꿈 문자인 **CR + LF** 가 스크립트에 적용이 되게 되는데, Linux/Unix OS 의 경우 줄바꿈 문자가 **LF** 이기 때문에 해당 스크립트를 정상적으로 인식하지 못하게 되는 것이다.



### 해결

`dos2unix` 라는 tool을 설치하여 파일의 OS 플랫폼 스타일을 변환해주면 간단하게 해결된다.

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



