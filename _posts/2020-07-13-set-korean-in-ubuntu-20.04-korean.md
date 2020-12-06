---
layout: post
published: true
title: '가상머신(VM) 우분투(ubuntu linux) 20.04 한글 설정'
date: '2020-07-13'
tags:
  - linux
  - ubuntu
  - 한글 설정
---
가상화 소프트웨어 VMware 나 VM Fusion 에서 지원하는 **빠른 설치** 옵션을 이용해서 우분투 20.04 운영체제를 가상머신 (VM) 에 설치했다면 기본 언어 설정이 영어로 되어 있어서 한글 입력은 커녕 한국어 언어팩도 설치되어 있지 않은 상태이다.  이럴 때에는 다음의 순서로 한글 설정을 진행한다.

1. Settings

    ![2020-07-13-set-korean-ubuntu-20-dot-04-01.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-01.png)

2. Region & Language → Manage Installed Languages

    ![2020-07-13-set-korean-ubuntu-20-dot-04-02.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-02.png)

3. Install

    ![2020-07-13-set-korean-ubuntu-20-dot-04-03.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-03.png)

4. Install / Remove Languages

    ![2020-07-13-set-korean-ubuntu-20-dot-04-04.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-04.png)

5. Korean 체크 & Apply

    ![2020-07-13-set-korean-ubuntu-20-dot-04-05.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-05.png)

6. Language 에 "한국어" 보임

    ![2020-07-13-set-korean-ubuntu-20-dot-04-06.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-06.png)

    > 만약 "한국어"가 안 보일 경우, Install / Remove Languages 에서 Korean 체크 해제 & Apply 로 한국어 언어팩을 제거한 다음 다시 Korean 체크  & Apply로 재 인스톨 하면 된다.

7. Language 에 "한국어" 를 드래그 & 드랍 으로 맨 위로 순서 바꿔주기 → Apply System-Wide

    ![2020-07-13-set-korean-ubuntu-20-dot-04-07.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-07.png)

8. Regional Formats 탭 → format 을 한국어로 변경 → Apply System-Wide → Close

    ![2020-07-13-set-korean-ubuntu-20-dot-04-08.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-08.png)

9. 재부팅

    ![2020-07-13-set-korean-ubuntu-20-dot-04-09.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-09.png)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-10.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-10.png)

10. 예전 이름 유지

    ![2020-07-13-set-korean-ubuntu-20-dot-04-11.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-11.png)

    > 한글로 폴더 이름을 업데이트 하는 부분은 본인의 선택이나 특정 유틸리티의 경우 경로 상에 한글이 들어가 있으면 설정이 제대로 안되는 경우가 있어서 "예전 이름 유지" 를 추천한다.



11. 설정

    ![2020-07-13-set-korean-ubuntu-20-dot-04-12.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-12.png)

12. 지역 및 언어 → 입력소스 에서 '+'

    ![2020-07-13-set-korean-ubuntu-20-dot-04-13.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-13.png)

13. 입력 소스 추가 - 한국어(Hangul)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-14.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-14.png)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-15.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-15.png)

14. 입력소스 - 영어(미국) 삭제

    ![2020-07-13-set-korean-ubuntu-20-dot-04-16.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-16.png)

15. 키보드 설정

    ![2020-07-13-set-korean-ubuntu-20-dot-04-17.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-17.png)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-18.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-18.png)

    입력소스를 한국어(Hangul)로 설정 하면 기본으로 설정되어 있는 한영전환키를 통해서 한글 입력이 가능하다. 기본으로 설정된 한영전환키는 `<Shift + Space>` 키나  `<Hangul>` 키 인데, 여기서 `<Hangul>` 키는    `<한/영>` 키를 말한다. 하지만, `<한/영>` 키가 따로 없고, `<Alt_R>` (오른쪽 alt) 키를 `<한/영>`키 대신 쓰는 경우는 추가 셋팅이 필요하다.

16. 한영전환키 추가 →  `<Alt_R>` 키 누르고 확인 → 적용 → 확인

    ![2020-07-13-set-korean-ubuntu-20-dot-04-19.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-19.png)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-20.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-20.png)

    ![2020-07-13-set-korean-ubuntu-20-dot-04-21.png]({{site.baseurl}}/assets/img/post_included/2020-07-13-set-korean-ubuntu-20-dot-04-21.png)

    만약, 다른 키를 사용하고 싶다면 해당 키를 추가해도 상관없다.
