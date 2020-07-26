---
layout: post
published: true
title: '[solved] ubuntu 도커 이미지 빌드 시 timezone 설정 방법'
date: '2020-07-26'
tags:
  - docker
  - timezone
  - 시간설정
  - troubleshooting
  - 오류 해결
  - ubuntu
---
최근 Docker를 이용한 작업이 많아지면서 여러 이슈들이 있었는데, 그 중에서  많은 삽질을 했던 도커 컨테이너 시간대 설정 방법을 공유한다.


### 상황

Dockerfile 을 이용해서 ubuntu docker image build 를 하게 되면 기본적으로 timezone 이 UTC로 되어 있다. 개발이나 간단한 로직 테스트 목적이라면 크게 문제가 되지 않지만, 시간과 관계되는 작업 (예 : 로그 출력 등) 을 하는 경우 timezone을 설정 해 주어야 한다.


### 해결

Dockerfile 에 다음의 라인을 추가 한다.

```docker
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Asia/Seoul

RUN apt-get install -y tzdata
```


### 참고 - 명령어 설명

- **DEBIAN_FRONTEND=noninteractive**  : tzdata 설치 시 사용자가 직접 timezone 설정을 할 수 있도록 입력할 수 있는 부분이 나오는데, 도커 이미지를 생성할 때는 입력을 할 수 없으므로 사용자의 입력 없이 넘어가기 위해 설정한다.
- **TZ=Asia/Seoul** : tzdata 는 시스템 환경변수 TZ 의 값으로 timezone을 설정하기 때문에 해당 환경 변수를 우리가 원하는 지역으로 설정한다.
- **ARG 와 ENV** : ARG 는 docker build 시에만 적용되는 변수 이며, ENV는 docker container 내부의 환경변수로 설정된다.
