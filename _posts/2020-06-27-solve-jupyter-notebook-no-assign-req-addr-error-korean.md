---
layout: post
published: true
title: '리눅스에서 Jupyter notebook 실행시 OSError: [Errno 99] Cannot assign requested address 에러 해결 방법'
date: '2020-06-27'
tags:
  - jupyter notebook
  - linux
  - 오류 해결
  - troubleshooting
---
### 상황
리눅스 환경에서 jupyter notebook 을 실행할 때, 다음의 에러 메시지를 보게 되는 경우가 있다.

> OSError: [Errno 99] Cannot assign requested address

```bash
$ jupyter notebook
Traceback (most recent call last):
  File "/usr/local/bin/jupyter-notebook", line 8, in <module>
    sys.exit(main())
  File "/usr/local/lib/python3.6/dist-packages/jupyter_core/application.py", line 270, in launch_instance
    return super(JupyterApp, cls).launch_instance(argv=argv, **kwargs)
  File "/usr/local/lib/python3.6/dist-packages/traitlets/config/application.py", line 663, in launch_instance
    app.initialize(argv)
  File "<decorator-gen-7>", line 2, in initialize
  File "/usr/local/lib/python3.6/dist-packages/traitlets/config/application.py", line 87, in catch_config_error
    return method(app, *args, **kwargs)
  File "/usr/local/lib/python3.6/dist-packages/notebook/notebookapp.py", line 1769, in initialize
    self.init_webapp()
  File "/usr/local/lib/python3.6/dist-packages/notebook/notebookapp.py", line 1490, in init_webapp
    self.http_server.listen(port, self.ip)
  File "/usr/local/lib/python3.6/dist-packages/tornado/tcpserver.py", line 151, in listen
    sockets = bind_sockets(port, address=address)
  File "/usr/local/lib/python3.6/dist-packages/tornado/netutil.py", line 174, in bind_sockets
    sock.bind(sockaddr)
OSError: [Errno 99] Cannot assign requested address
```   

### 원인
jupyter notebook을 실행할 때 IP 설정을 해주지 않아서 이 문제가 발생한다.

### 해결
`jupyter notebook 을 실행`할 때 `IP 와 Port 를 설정`해준다.

> jupyter notebook --ip=0.0.0.0 --port=8888 --allow-root

```bash
$ jupyter notebook --ip=0.0.0.0 --port=8888 --allow-root
[I 11:25:45.432 NotebookApp] JupyterLab extension loaded from /usr/local/lib/python3.6/dist-packages/jupyterlab
[I 11:25:45.432 NotebookApp] JupyterLab application directory is /usr/local/share/jupyter/lab
[I 11:25:45.445 NotebookApp] Serving notebooks from local directory: /code
[I 11:25:45.445 NotebookApp] The Jupyter Notebook is running at:
[I 11:25:45.445 NotebookApp] http://e999943e0fff:8888/?token=3c3fb4baaaaaaaaaa387c52d6fd2f6aaaaaaaaaa6d761c01
[I 11:25:45.445 NotebookApp]  or http://127.0.0.1:8888/?token=3c3fb4baaaaaaaaaa387c52d6fd2f6aaaaaaaaaa6d761c01
[I 11:25:45.446 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[W 11:25:45.458 NotebookApp] No web browser found: could not locate runnable browser.
[C 11:25:45.459 NotebookApp]

    To access the notebook, open this file in a browser:
        file:///root/.local/share/jupyter/runtime/nbserver-20-open.html
    Or copy and paste one of these URLs:
        http://e999943e0fff:8888/?token=3c3fb4baaaaaaaaaa387c52d6fd2f6aaaaaaaaaa6d761c01
     or http://127.0.0.1:8888/?token=3c3fb4baaaaaaaaaa387c52d6fd2f6aaaaaaaaaa6d761c01
```
