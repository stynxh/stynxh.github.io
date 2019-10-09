---
layout: post
published: true
title: Docker 에 Selenium 과 Chrome 브라우저 실행환경 셋팅
date: '2019-10-09'
category:
  - research
tags:
  - docker
  - selenium
  - chrome
  - chromedriver
  - python
---
## google chrome 설치

```bash
# apt-get -y update
# apt-get install -y google-chrome-stable
```  

## chromedriver 설치

```bash
# apt-get install -yqq unzip curl
# wget -O /tmp/chromedriver.zip http://chromedriver.storage.googleapis.com/`curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE`/chromedriver_linux64.zip
# unzip /tmp/chromedriver.zip chromedriver -d /usr/local/bin/ 
```  

## selenium 설치

```bash
# apt-get install -y python3 python3-pip
# pip3 install selenium
```

## python 실행코드

```python
from selenium import webdriver

options = webdriver.ChromeOptions()
options.add_argument('--headless')
# options.add_argument('window-size=1200x600')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')

browser = webdriver.Chrome(chrome_options=options)
#chrome드라이버가 PATH 환경변수 설정이 되어있지 않다면 executable_path 옵션으로 chromedriver 위치 지정
#browser = webdriver.Chrome(chrome_options=options, executable_path="/usr/local/bin/chromedriver")

url = "http://google.com"

browser.get(url)
browser.save_screenshot("Website.png")
browser.quit()
```
