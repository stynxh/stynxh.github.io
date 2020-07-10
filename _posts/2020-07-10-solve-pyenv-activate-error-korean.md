---
layout: post
published: true
title: 'pyenv activate 실행시 "Failed to activate virtualenv." 에러 메시지 해결법'
date: '2020-07-10'
tags:
  - python
  - pyenv
  - pyenv-virtualenv
  - error
---
### 상황

pyenv 와 pyenv-virtualenv 를 설치한 후  pyenv activate 를 실행시키려고 할 때, 다음과 같은 에러 메시지를 보게 되는 경우가 있다.

{: .box-error}
Failed to activate virtualenv.  
Perhaps pyenv-virtualenv has not been loaded into your shell properly.  
Please restart current shell and try again.



### 해결

`Shell profile` 파일에서 다음의 사항을 확인할 것.

{: .box-note}
**Shell profile 파일:** 각자의 쉘 구성 환경에 따라 다르며 ~/.zshrc, ~/.bash_profile, ~/.bashrc 등이 있다.

```bash
$ cat ~/.zshrc
...
...
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"

if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi

eval "$(pyenv virtualenv-init -)"
```

위의 내용이 모두 적용되어 있어야 하며, 특히 `eval "$(pyenv init -)"` 부분과 `eval "$(pyenv virtualenv-init -)"` 부분은 $PATH 를 다시 계산하여야 하므로 `Shell profile  파일의 가장 마지막에 위치` 해야 한다. 꼭 순서를 맞춰서 작성해야 한다.
