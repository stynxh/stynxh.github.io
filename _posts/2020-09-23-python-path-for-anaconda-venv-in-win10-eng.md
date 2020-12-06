---
layout: post
published: true
title: 'Location of python for anaconda virtual environment in Windows10'
date: '2020-09-23'
tags:
  - Anaconda
  - Windows10
  - python
---

### Test environment

- Windows10
- Anaconda 3.7 64bit (2020.02)

### Location of python for anaconda virtual environment

If you installed anaconda with **default**, the location is as follow.

> `C:\Users\[account]\anaconda3\envs\venv[virtual environment name]`                                     
> ex) C:\Users\stynxh\anaconda3\envs\venv


If it is not the above location, please check `C:\Users\[account]\.conda\environments.txt` file.

```
C:\Users\stynxh\anaconda3
C:\Users\stynxh\anaconda3\envs\venv
C:\Users\stynxh\anaconda3\envs\tf1.15
C:\Users\stynxh\anaconda3\envs\dev
```

Alternatively, after activating the virtual environment in **Anaconda Prompt** (not Anaconda Powershell), run `where python` command.

```powershell
(base) C:\Users\stynxh>conda activate venv

(venv) C:\Users\stynxh>where python
C:\Users\stynxh\anaconda3\envs\venv\python.exe
C:\Users\stynxh\AppData\Local\Programs\Python\Python37-32\python.exe
C:\Users\stynxh\AppData\Local\Microsoft\WindowsApps\python.exe
```
