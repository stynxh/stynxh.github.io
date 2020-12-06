---
layout: post
published: true
title: 'Windows10 Anaconda 가상환경 파이썬 위치'
date: '2020-09-23'
tags:
  - Anaconda
  - Windows10
  - python
---

### 작업환경

- Windows10
- Anaconda 3.7 64bit (2020.02)

### 가상환경 파이썬 위치

Anaconda를 **기본설정** 으로 설치했다면, 위치는 다음과 같다.

> `C:\Users\[계정명]\anaconda3\envs\venv[가상환경 이름]`                                     
> ex) C:\Users\stynxh\anaconda3\envs\venv


만약, 위 경로가 아닐 경우 `C:\Users\[계정명]\.conda\environments.txt` 파일을 확인하면 가상환경의 위치를 알 수 있다.

```
C:\Users\stynxh\anaconda3
C:\Users\stynxh\anaconda3\envs\venv
C:\Users\stynxh\anaconda3\envs\tf1.15
C:\Users\stynxh\anaconda3\envs\dev
```

또는, **Anaconda Prompt** (Anaconda Powershell 아님) 에서 가상환경을 활성화 시킨 후, `where python` 명령을 수행한다.

```powershell
(base) C:\Users\stynxh>conda activate venv

(venv) C:\Users\stynxh>where python
C:\Users\stynxh\anaconda3\envs\venv\python.exe
C:\Users\stynxh\AppData\Local\Programs\Python\Python37-32\python.exe
C:\Users\stynxh\AppData\Local\Microsoft\WindowsApps\python.exe
```
