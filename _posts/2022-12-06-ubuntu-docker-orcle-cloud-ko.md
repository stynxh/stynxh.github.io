---
layout: post
published: true
title: '오라클 클라우드 우분투에서 도커를 이용하여 웹서버 올리기'
date: '2022-12-06'
tags:
  - oracle cloud
  - ubuntu
  - docker
---
오라클 클라우드 우분투에서 도커를 이용하여 웹서버를 돌리려고 했더니, 클라우드 방화벽 뿐만이 아니라 내 우분투 서버에서도 방화벽을 설정해야 한다고 하더라. 구글링해보니 iptables로 하는 방법은 많이 나와있던데 명령어가 복잡하기도 하고 잘 안되기도 해서, 간단한 방법을 찾다가 ufw로 하는 방법을 발견했다. 

---
**$> Table-of-Contents_**

* TOC
{:toc}
---

# 0. 테스트 환경

- 오라클 클라우드 compute instance (무료 요금제 기본 셋팅)
- ubuntu 22.04

# 1. VCN(Virtual Cloud Networks) security list 규칙 추가

1. 네비게이션 메뉴에서, **네트워킹** 클릭 후, **가상 클라우드 네트워크** 클릭.
2. VCN 클릭(vcn-2022xxxx-1234 처럼 되어있음).
3. 왼쪽 서브메뉴 **리소스**에서 **보안 목록** 클릭.
4. **Default Security List** 클릭.
5. **수신규칙 추가** 클릭 후 아래와 같이 입력:
    - **소스 유형:** CIDR
    - **소스 CIDR**: 0.0.0.0/0
    - **IP 프로토콜:** TCP
    - **소스 포트 범위:** All
    - **대상 포트 범위:** 80
    - **수신 규칙 추가** 버튼 클릭.

자세한 내용은 다음의 링크를 참조 바람
- [https://docs.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm](https://docs.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm)  
- [https://docs.oracle.com/en/learn/lab_compute_instance/index.html](https://docs.oracle.com/en/learn/lab_compute_instance/index.html)

# 2. ssh를 이용하여 우분투 시스템에 접속 후 ufw 설정

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

# 3. 필요 패키지 설치 및 git clone

```bash
> sudo apt install -y git docker.io docker-compose
> git clone https://github.com/<user>/<repository>.git
> cd <repository>
```

# 4. 도커 컨데이너 실행

```bash
> sudo docker-compose up --build -d
> docker ps -a
```