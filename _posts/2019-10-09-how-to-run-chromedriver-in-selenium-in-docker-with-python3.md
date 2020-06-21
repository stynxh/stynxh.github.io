---
layout: post
published: true
title: How to run chromedriver in selenium in docker with python3
date: '2019-10-09'
category:
  - research
tags:
  - selenium
  - chrome
  - chromedriver
  - docker
  - python
---
## install google chrome

```bash
# apt-get -y update
# apt-get install -y google-chrome-stable
```  

If you see the following error message when installing the Chrome browser,

{: .box-error}
E: Unable to locate package google-chrome-stable

refer to [Install Google Chrome on Ubuntu linux from command line](../2020-06-21-install-google-chrome-on-ubuntu-linux-from-command-line-eng/) document.


## install chromedriver

```bash
# apt-get install -yqq unzip curl
# wget -O /tmp/chromedriver.zip http://chromedriver.storage.googleapis.com/`curl -sS chromedriver.storage.googleapis.com/LATEST_RELEASE`/chromedriver_linux64.zip
# unzip /tmp/chromedriver.zip chromedriver -d /usr/local/bin/ 
```  

## install selenium

```bash
# apt-get install -y python3 python3-pip
# pip3 install selenium
```

## python code

```python
from selenium import webdriver

options = webdriver.ChromeOptions()
options.add_argument('--headless')
# options.add_argument('window-size=1200x600')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')

browser = webdriver.Chrome(chrome_options=options)
#If the chromedriver is not set in the PATH environment variable, specify the chromedriver location with the executable_path option.
#browser = webdriver.Chrome(chrome_options=options, executable_path="/usr/local/bin/chromedriver")

url = "http://google.com"

browser.get(url)
browser.save_screenshot("Website.png")
browser.quit()
```
