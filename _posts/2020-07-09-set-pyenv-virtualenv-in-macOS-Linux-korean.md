---
layout: post
published: true
title: 'pyenv 및  pyenv-virtualenv 로 python 개발환경 구축하기 - macOS, Linux'
date: '2020-07-09'
tags:
  - macOS
  - linux
  - pyenv
  - pyenv-virtualenv
  - python
  - 개발환경
---

python 으로 코딩을 하다보면 python 자체의 버전 문제가 발생하기도 하지만 워낙 라이브러리가 많기 때문에 라이브러리의 버전 문제가 발생하기도 한다. 따라서, python 개발 환경은 가상환경으로 구축하는게 필수이다.   

이에 따라, 이 문서에서는 `pyenv` 및 `pyenv-virtualenv` 로 python 개발 환경을 구축하는 과정을 설명한다.

### 테스트 환경

- OS : macOS Catalina, Ubuntu Linux 20.04
- SHELL : zsh

### PYENV 설치

1. homebrew 를 이용하여 설치 ( macOS 의 경우만 해당하며, 맥 유저의 경우 추천함 )

    ```bash
    brew update
    brew install pyenv
    ```

2. git clone 을 이용하여 설치 ( macOS, Linux 둘다 해당)

    ```bash
    git clone https://github.com/pyenv/pyenv.git ~/.pyenv
    ```

### PYENV 설정

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
exec "$SHELL"
```

### PYENV 실행

```bash
pyenv install 3.8.3
pyenv global 3.8.3
```

### VIRTUALENV 설치

1. homebrew 를 이용하여 설치 ( macOS 의 경우만 해당하며, 맥 유저의 경우 추천함 )

    ```bash
    brew update
    brew install pyenv-virtualenv
    ```

2. git clone 을 이용하여 설치 ( macOS, Linux 둘다 해당)

    ```bash
    git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
    ```

### VIRTUALENV 설정

```bash
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
exec "$SHELL"
```

### 가상환경 생성

```bash
pyenv virtualenv 3.5.3 <name>
```

{: .box-note}
**Note:** pyenv install 로 설치된 버전만 가상 환경 생성 가능함

### 가상환경 실행 및 해제

```bash
pyenv activate <name>
pyenv deactivate
```

### 참고

- [https://github.com/pyenv](https://github.com/pyenv/)/
- [https://github.com/pyenv/pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)
- [https://opensource.com/article/19/5/python-3-default-mac](https://opensource.com/article/19/5/python-3-default-mac)
