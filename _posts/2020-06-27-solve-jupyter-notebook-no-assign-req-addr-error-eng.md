---
layout: post
published: true
title: 'How to fix "OSError: [Errno 99] Cannot assign requested address" error when running Jupyter notebook on Linux'
date: '2020-06-27'
tags:
  - jupyter notebook
  - linux
  - troubleshooting
---
### Situation
When running jupyter notebook on Linux , you may see the following error message.

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

### Cause
This problem is caused by not setting the IP address when running jupyter notebook.

### Solution
When running jupyter notebook, `set IP address and Port number`.

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
