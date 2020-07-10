---
layout: post
published: true
title: Install Google Chrome on Ubuntu linux from command line
date: '2020-06-21'
tags:
  - ubuntu
  - linux
  - chrome
---
### STEP 1. edit **sources.list** file

```bash
sudo vi /etc/apt/sources.list
```
Add and save the following sources at the end of the **sources.list** file

```
...
...
...
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```



### STEP 2. Download Google's signing key

```bash
sudo apt-get install wget
wget https://dl.google.com/linux/linux_signing_key.pub
```



### STEP 3. Google Chrome authentication key added to apt package manager

```bash
sudo apt-get install gnupg
sudo apt-key add linux_signing_key.pub
```



### STEP 4. apt update and install google chrome

```bash
sudo apt update
sudo apt install google-chrome-stable
```



### + Appendix
If you see the following warning message when doing an apt update,

{: .box-warning}
Target Packages (main/binary-amd64/Packages) is configured multiple times

This is because the Google Chrome package creates a special file **/etc/apt/sources.list.d/google-chrome.list**, which can be fixed by deleting this file.
```bash
sudo rm /etc/apt/sources.list.d/google-chrome.list
```  
