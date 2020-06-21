---
layout: post
published: true
title: 우분투 리눅스에서 커맨드라인으로 구글 크롬 (chrome) 설치하기
tags:
  - ubuntu
  - linux
  - google chrome
  - chrome
  - install
  - chrome install
date: '2020-06-21'
---
### STEP 1. sources.list 수정
```bash
sudo vi /etc/apt/sources.list
```
sources.list 파일의 마지막에 다음의 소스 추가 및 저장
```
...
...
...
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```  
   
  
### STEP 2. Google signing key 다운로드
```bash
sudo apt-get install wget
wget https://dl.google.com/linux/linux_signing_key.pub
```  
  
  
### STEP 3. apt 패키지 매니저에 google 크롬 인증키 추가
```bash
sudo apt-get install gnupg
sudo apt-key add linux_signing_key.pub
```  
  
  
### STEP 4. apt 업데이트 및 구글 크롬 설치

```bash
sudo apt update
sudo apt install google-chrome-stable
```  
  
  
### + 부록
만약 apt update 를 할 때, 다음과 같은 경고 메시지를 본다면
{: .box-warning} 
Target Packages (main/binary-amd64/Packages) is configured multiple times

이것은 구글 크롬 패키지가 특수한 파일 **/etc/apt/sources.list.d/google-chrome.list** 을 생성하기 때문인데 이 파일을 삭제하면 해결할 수 있다.
```bash
sudo rm /etc/apt/sources.list.d/google-chrome.list
```  
  
  


