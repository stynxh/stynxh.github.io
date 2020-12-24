---
layout: post
published: true
title: 'Docker Desktop으로 Windows10 Home 도커 설치하기 - Docker Toolbox deprecated'
date: '2020-12-24'
tags:
  - Windows10
  - docker
---
Windows10 Home 에 도커를 설치하면서 기존에 익숙했던 방법인 Docker Toolbox 를 더 이상 이용할 수 없기 때문에 새로운 방법인 Docker Desktop을 이용해서 설치하는 방법을 설명한다.

---
**$> Table-of-Contents_**

* TOC
{:toc}
---

## Docker Toolbox란?

2020년 초까지만 해도 Windows OS에 도커를 설치하는 방법은 크게 2가지 였다. 첫번째는 Windows10 Pro 버전 이상에서만 사용할 수 있는 Docker Desktop 을 이용해 설치하는 방법이고, 두번째는 Windows10 Home 이하 (Windows7 포함) 버전에서 사용되는 Docker Toolbox 를 이용해서 설치하는 방법이다. 결국, `Windows 버전에 따라서 설치 파일이 Docker Desktop 과 Docker Toolbox 2가지` 였다는 이야기이다.

## Windows10 Home 에서 Docker Toolbox 설치 오류

2020년 12월 현재, 확인 결과 Windows10 Home 에서 Docker Toolbox를 이용해 도커를 설치하려고 하면 오류가 발생한다. 그 이유는 도커 Toolbox가 Deprecated 되었기 때문이다.

> **사용되지 않음**  
Docker Toolbox는 더 이상 사용되지 않으며 더 이상 개발 중이 아닙니다. 대신 Docker Desktop을 사용하십시오

참고: [Docker 공식 문서](https://docs.docker.com/docker-for-windows/docker-toolbox/)

## Windows10 Home에서 Docker Desktop으로 도커 설치하기

### 시스템 요구사항

- Windows 10, 버전 1903 이상
- Windows에서 WSL 2 기능을 활성화
- Windows 10 Home에서 WSL 2를 성공적으로 실행하려면 다음 하드웨어 필수 구성 요소가 필요
    - SLAT (Second Level Address Translation) 기능이있는 64 비트 프로세서
    - 4GB 시스템 RAM
    - BIOS 수준 하드웨어 가상화 지원은 BIOS 설정에서 활성화해야함
- Linux 커널 업데이트 패키지를 다운로드하여 설치

### WSL란?

Windows Subsystem for Linux 의 약어로 윈도우 10에서 네이티브로 리눅스 실행 파일(ELF)을 실행하기 위한 호환성 기술이다. 쉽게 미니 가상머신 같은 거라고 생각하면 편할 것 같다. 도커는 애초에 Linux 재단에서 탄생한 기술이기 때문에 도커를 실행시키기 위해서는 리눅스 환경이 구성되어야 했고, 이전에 Docker Toolbox에서는 이를 Oracle Virtualbox 와 MinGW 로 리눅스 환경을 구성했다. (개인적으로 Docker Toolbox 를 사용해본 결과 안정성에 문제가 많았다.) 하지만, Docker Desktop에는 이 WSL을 사용함으로써, 도커의 안정성을 끌어올린 것으로 보인다. 사실상 백엔드에서는 이 WSL 기술이 핵심이라고 할 수 있겠다.

### 설치 순서

1. [Linux 커널 업데이트 패키지](https://docs.microsoft.com/ko-kr/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package)를 다운로드하여 설치한다.
2.  **[Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) 에서 Docker Desktop Installer.exe** 를 다운로드 후 설치 **프로그램** 을 실행한다.
3. 메시지가 표시되면 구성 페이지에서 **WSL 2 기능 사용** 옵션이 선택 되었는지 확인한다.
4. 설치 마법사의 지침에 따라 설치 프로그램을 인증하고 설치를 계속한다.
5. 설치가 완료되면 **닫기** 를 클릭 하여 설치 프로세스를 완료한다.

## 참고

도커 공식 홈페이지의 [Windows Home에 Docker Desktop 설치](https://docs.docker.com/docker-for-windows/install-windows-home/) 문서
