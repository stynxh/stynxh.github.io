---
layout: post
published: true
title: 'Install docker on Windows10 Home with Docker Desktop - Docker Toolbox deprecated'
date: '2020-12-24'
tags:
  - Windows10
  - docker
---
This post is explain that installing docker on Windows 10 Home using Docker Desktop. Because Docker Toolbox is no longer available.

---
**$> Table-of-Contents_**

* TOC
{:toc}
---

## What is Docker Toolbox?

Until early 2020, there were two main ways to install Docker on Windows OS. The first is to install using Docker Desktop, which can only be used with Windows 10 Pro version or higher, and the second is to install using Docker Toolbox, which is used in Windows 10 Home or lower (including Windows 7). In the end, it is said that `there are two installation files, Docker Desktop and Docker Toolbox`, depending on the Windows version.

## Docker installation error with Docker Toolbox on Windows 10 Home

As of December 2020, show an error when attempting to install Docker using Docker Toolbox on Windows 10 Home. Because the Docker Toolbox has been deprecated.

> **Deprecated**  
Docker Toolbox has been deprecated and is no longer in active development. Please use Docker Desktop instead

Reference: [Docker docs](https://docs.docker.com/docker-for-windows/docker-toolbox/)

## Installing Docker with Docker Desktop on Windows 10 Home

### System Requirements
- Install Windows 10, version 1903 or higher.
- Enable the WSL 2 feature on Windows.
- The following hardware prerequisites are required to successfully run WSL 2 on Windows 10 Home:
    - 64 bit processor with Second Level Address Translation (SLAT)
    - 4GB system RAM
    - BIOS-level hardware virtualization support must be enabled in the BIOS settings.
- Download and install the Linux kernel update package.

### What is WSL?

WSL(Windows Subsystem for Linux) is a compatibility layer for running Linux executable files (ELF) natively in Windows 10. It would be easy to think of it as something like a mini virtual machine. Docker was originally a technology born by the Linux Foundation, so in order to run Docker, a Linux environment had to be configured. Previously, Docker Toolbox configured a Linux environment with Oracle Virtualbox and MinGW. (Personally, as a result of using Docker Toolbox, there were many problems with stability.) However, it seems that Docker's stability has been improved by using this WSL for Docker Desktop. In fact, in the back end, this WSL technology can be said to be the key.

### Install

1) Download and install the [Linux kernel update package](https://docs.microsoft.com/windows/wsl/wsl2-kernel).  
2)  Download **Docker Desktop Installer.exe** from [Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) and to run the installer.  
3) When prompted, ensure the **Enable WSL 2 Features** option is selected on the Configuration page.  
4) Follow the instructions on the installation wizard authorize the installer and proceed with the install.  
5) When the installation is successful, click Close to complete the installation process.  

## Reference

[Install Docker Desktop on Windows Home](https://docs.docker.com/docker-for-windows/install-windows-home/) from docker docs.
