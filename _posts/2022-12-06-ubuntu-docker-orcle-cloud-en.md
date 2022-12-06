---
layout: post
published: true
title: 'The easy way run web server using ubuntu docker container on oracle cloud'
date: '2022-12-06'
tags:
  - oracle cloud
  - ubuntu
  - docker
---
This article is about run web server using ubuntu docker container on oracle cloud. I don’t use IPTABLES. I use only `UFW`(Uncomplicated Firewall). 

---
**$> Table-of-Contents_**

* TOC
{:toc}
---

# 0. Test envirionment

- Oracle cloud compute instance (default set for always free)
- ubuntu 22.04

# 1. Add VCN(Virtual Cloud Networks) security list rule

1. Open the navigation menu, click **Networking**, and then click **Virtual Cloud Networks**.
2. Click the VCN you're interested in.
3. Under **Resources**, click **Security Lists**.
4. Click on the **Default Security List**.
5. Here you need to open port 80. Click on **+ Another Ingress Rule** and add the following values as shown below:
    - **Source Type:** CIDR
    - **Source CIDR**: 0.0.0.0/0
    - **IP Protocol:** TCP
    - **Source Port Range:** All
    - **Destination Port Range:** 80
    - Click on **Add Ingress Rules** at the bottom.

More details, please refer to [https://docs.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm](https://docs.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm) and [https://docs.oracle.com/en/learn/lab_compute_instance/index.html](https://docs.oracle.com/en/learn/lab_compute_instance/index.html)

# 2. Connect to ubuntu system using ssh and set ufw

```bash
> sudo apt update
> sudo ufw allow 22
> sudo ufw allow 80
> yes | sudo ufw enable
> sudo systemctl enable ufw.service
> sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
80 (v6)                    ALLOW       Anywhere (v6)
```

# 3. Install pakage and git clone

```bash
> sudo apt install -y git docker.io docker-compose
> git clone https://github.com/<user>/<repository>.git
> cd <repository>
```

# 4. Run docker container

```bash
> sudo docker-compose up --build -d
> docker ps -a
```