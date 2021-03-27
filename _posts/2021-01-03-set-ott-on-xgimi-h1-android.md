---
layout: post
published: true
title: '진성 애플빠의 XGIMI H1 (안드로이드 TV OS)빔프로젝터 OTT시스템 구축기'
date: '2021-01-03'
tags:
  - Android
  - XGIMI H1
  - OTT
---
이 이야기는 안드로이드 기기는 한번도 써 본 적이 없는 `진성 애플빠`가 TV 대용으로 사용하는 `XGIMI H1 빔프로젝터` (Android 5.1.1)에 OTT 시스템 (`Tving, Wavve, Netflix, Youtube, Naver sports`)을 나름 성공적으로 구축한 삽질기 이다.

---
**$> Table-of-Contents_**

* TOC
{:toc}
---

# 사건의 배경

나는 맥북, 아이패드, 아이폰, 애플워치를 사용하는 진성 애플빠 이다. (그렇다. 우리집은 사과농장이다.) 그래서 2년전 TV대용으로 사용할 XGIMI H1 프로젝터를 사놓고도, 기본 앱스토어 (APTOIDE) 에서 내가 즐겨보는 tving, wavve(그 당시에는 pooq)가 설치 및 동작되지 않아서 "중국에서 만들어서 우리나라 앱이 잘 안돌아가나보다" 생각하고 그 동안 노트북을 연결해서 순수한 빔프로젝터로만 사용했다.

# 현실에 대한 의구심

그러다가 최근에 빔 프로젝터와 연결된 노트북의 펜 소리가 거슬리기 시작(언제든지 드라마나 예능을 시청하기 위해서 노트북은 24시간 켜져있었다) 하면서 "왜 저렇게 써야만 하지? 쟤도 분명 안드로이드 OS가 들어가 있는데, 뭔가 방법이 있지 않을까?" 해서 구글링을 시작했다.

# 놀라운 안드로이드의 세계

구글링을 하다보니 알게된 놀라운 사실은 안드로이드는 공식 앱스토어를 통하지 않아도 그냥 웹에서 검색해서 APK (안드로이드 실행파일) 파일을 다운받아서 설치할 수 있었다!! 안드로이드를 계속 썼던 사람이라면 너무 당연한 이야기 일수도 있는데, 서두에도 이야기 했듯이 나는 진성 애플빠 이다. 그렇기 때문에 `앱스토어에서 받지 않은 파일 == 약간 이상한 파일` 이라는 공식이 자연스러웠기 때문에 정상적인 파일도 그냥 인터넷에서 받아서 설치하는 안드로이드 시스템이 놀라웠다. 기존에 가지고 있던 편견이 깨지면서 무한한 자유도가 펼쳐졌고, 그것이 삽질의 시작이었다.

# 각종 OTT 구축 삽질기

해당 섹션은 각 OTT 시스템에 대한 삽질기 이니, 순서대로 읽지 않아도 되고, 필요한 부분만 읽어도 무방하다.

- [Netflix](#aptoide-에서-넷플릭스-설치)
- [Youtube (2021.03.27 업데이트)](#xgimi-네이버-카페를-통한-스마트-유튜브-설치-20210327-업데이트)
- [Naver Sports Live](#xgimi-h1-프로젝터에서-크롬-웹브라우저를-통한-네이버-스포츠-live-시청)
- [Tving](#kodi-애드온으로-tving-wavve-시청하기)
- [Wavve](#kodi-애드온으로-tving-wavve-시청하기)
- [Watcha (실패)](#xgimi-h1-프로젝터에서-watcha-시청-하기-실패)  
    &#43;  
- [한글 키보드](#xgimi-h1-프로젝터에-한글-키보드-설정)

## APTOIDE 에서 넷플릭스 설치

자체 앱스토어인 APTOIDE 에서 넷플릭스 앱을 설치할 수 있었다. 그 외의 앱들은 프로젝터에 설치된 (지워지지도 않는) 구글 플레이스토어의 버전이 낮아서 설치가 되지 않았다.

## ~~XGIMI 네이버 카페를 통한~~ 스마트 유튜브 설치 (2021.03.27 업데이트)

XGIMI H1 프로젝터에는 유튜브 앱이 내장되어 있다. 하지만, 이 앱을 실행하면 버전이 낮아서 실행이 되지 않는다. (그렇다고 업데이트가 되는것도 아니고, 지워지지도 않는다. ㅡㅡ;;) ~~이를 해결하고자 검색하다가, 네이버 카페에  [XGIMI,Touyinger 중국직구 빔프로젝터 공식카페](https://cafe.naver.com/beampow) 를 알게 되었다. 이곳에서 여러 능력자 분들의 도움을 많이 받았는데, 그 중에 유튜브 앱을 약간 커스터마이징 해서 잘 작동할 수 있게 `스마트 유튜브` 라는 이름으로 다시 만들어서 올려주신 분이 있어서 해당 앱을 다운로드 받아서 설치했다.~~

~~- 스마트 유튜브 : 카페 가입 및 "스마트 유튜브" 검색 후 다운로드~~   
2021.03.27 확인 결과, 스마트 유튜브가 정상동작하지 않아서 해결방법을 찾아보니 [스마트 유튜브 공식 웹페이지](https://smartyoutubetv.github.io/)에서 최신 버전을 다운로드 할 수 있으나, [스마트 유튜브 깃헙 페이지](https://github.com/yuliskov/SmartYouTubeTV) 에 따르면 해당 앱은 더 이상 업데이트 되지 않으며, `스마트튜브넥스트` 라는 새로운 앱을 배포하고 있다고 한다.
> `Deprecation Notice`  
> This app is no longer updated.  
> For a better YouTube experience on Android TV check out SmartTubeNext     

실제로 최신버전의 스마트 유튜브를 설치해봐도 정상동작 하지 않는것은 마찬가지 였으며, 개발자가 새로 배포하는 `스마트튜브넥스트` 를 설치해보니 정상적으로 동작하였다.

- [스마트튜브넥스트](https://github.com/yuliskov/SmartTubeNext) 페이지에서 최신버전을 다운로드

## XGIMI H1 프로젝터에서 크롬 웹브라우저를 통한 네이버 스포츠 Live 시청

XGIMI H1 프로젝터에는 구글 크롬 웹브라우저가 내장되어 있다. 이 브라우저를 통해서 네이버 스포츠 웹페이지에 접속해서 Live 중계 영상을 바로 시청할 수 있다. 네이버 스포츠는 Windows OS에서 Live 중계를 시청할 경우 별도의 프로그램을 설치해야만 고화질(HD) 영상을 볼 수 있는데, Windows OS를 제외한 다른 운영체제 (MacOS, Linux, iOS, Android 등)에서는 별도의 프로그램 설치 없이 고화질(HD) 영상을 볼 수 있다. 따라서, 우리 프로젝터는 Android TV 운영체제 이기 때문에 별도의 프로그램 설치 없이 내장된 크롬 웹 브라우저를 통해서 네이버 스포츠 Live 중계 영상을 시청할 수 있다.

## KODI 애드온으로 Tving, Wavve 시청하기

### KODI 소개 및 설치하기

열심히 구글링을 하다보니 많은 사람들이 Android TV 운영체제에서는 우리나라 OTT 서비스들이 잘 동작하지 않기 때문에, `KODI` 라는 것을 설치해서 사용한다는 글을 많이 봤다. [KODI](https://kodi.tv/) 는 오픈소스 홈 시어터 소프트웨어이며, 이 소프트웨어를 설치하고 거기에 각 방송국 또는 OTT 를 플러그인 형태로 등록해서 내가 원하는 Tving 이나 Wavve 를 볼 수 있다는 것이다.

![2021-01-03-set-ott-on-xgimi-h1-android-01.png]({{site.baseurl}}/assets/img/post_included/2021-01-03-set-ott-on-xgimi-h1-android-01.png)

KODI 다운로드 및 설치, 한글 설정 방법은 다음의 블로그 포스팅을 참고하였다.

> [KODI 설치하고 한글 설정 및 애드온 추가하기](https://delightwook.tistory.com/56)

[출처 : delightwook 님 블로그]

추가로, 2021.01월 현재 다운로드해야 하는 KODI 버전은 위 블로그에 나와있는 대로 Recommended 버전이 아닌 Pre release 버전(v19)을 설치해야 한다. 왜냐하면, 앞으로 우리가 설치할 Tving 등의 애드온이 v19 버전만 지원하기 때문이다. 참고로, XGIMI H1은 32bit 시스템이기 때문에 `ARMV7A (32BIT) 를 다운`받아야 한다.

![2021-01-03-set-ott-on-xgimi-h1-android-02.png]({{site.baseurl}}/assets/img/post_included/2021-01-03-set-ott-on-xgimi-h1-android-02.png)

### KODI에 Tving, Wavve 애드온 설치하기

KODI를 설치했으면 이제 KODI에 Tving 및 Wavve 애드온을 설치해야 한다. 이는 다음의 블로그 포스팅을 참고하였다.

> [미박스 KODI 애드온 설치해 티빙, 웨이브 무료 실시간 방송 보는법](https://yoons-family.tistory.com/272)

[출처 : 허니듀크 님 블로그]

위의 블로그에도 나와있지만 실제 Tving, Wavve 등의 애드온을 개발 및 제공하시는 분은 밤보리 님으로 애드온 다운로드 주소는 다음과 같다. (아래에는 티빙 애드온 링크만 걸어놨지만 해당 애드온이 티빙, 웨이브 등을 다 지원한다.)

> [티빙 애드온 for Kodi](https://github.com/kym1088/tvingM)

## XGIMI H1 프로젝터에서 Watcha 시청 하기 (실패)

XGIMI H1 프로젝터에서 Watcha 를 보려고 시도해본 방법은 크게 2가지 이다.

- 안드로이드TV용 Watch 앱 설치
- KODI에 Watcha 애드온 설치 ([KODI에 Tving, Wavve 애드온 설치하기](#kodi에-tving-wavve-애드온-설치하기) 참고 - 밤보리님의 해당 애드온은 Tving, Wavve, Watcha 등의 통합 애드온이다.)

하지만, 위의 2가지 방법 다 로그인은 제대로 되고 영상 목록도 다 뜨지만, 영상을 플레이하면 플레이가 제대로 되지 않았다. KODI의 Watcha 애드온의 경우 함께 설치한 Tving와 Wavve는 되는데, Watcha 만 안되서 개발자인 밤보리님께 [오류 제보](https://github.com/kym1088/watchaM/issues/2)도 해보았으나, 이상이 없다는 답변을 받았다. 그래서 열심히 오류 로그도 보고 검색해본 결과, `XGIMI H1 프로젝터에서는 Watcha 시청이 불가능 하다는 결론`을 얻었다.

### XGIMI H1 프로젝터에서 Watcha 시청이 불가능한 이유

오류 로그를 분석해보면 가장 처음 에러가 발생하는 부분은 다음과 같다.

```bash
2020-12-23 16:04:07.994 T:24184 ERROR : AddOnLog: inputstream.adaptive: Key system request: com.widevine.alpha
```

여기서 문제가 되는 부분은 [widevine](https://en.wikipedia.org/wiki/Widevine) 패키지인데, `widevine` 은 DRM 기술로서, 디지털 저작권에 관련된 기술을 구현해놓은 라이브러리 패키지이다. 만약 영상이 widevine DRM 기술을 사용한다면, 그 영상을 플레이하려는 디바이스가 windevine DRM 인증을 받아야만 정상적인 플레이가 가능하다. 이 인증은 유저가 따로 신청해서 받는게 아니라 디바이스가 출시될 때, 인증이 적용되서 나온다. 이를 확인하는 방법은 [DRM Info](https://play.google.com/store/apps/details?id=com.androidfung.drminfo&hl=ko&gl=US) 라는 앱을 통해서 확인할 수 있다. 해당 앱을 설치하고 실행해보면 widevine이 적용된 디바이스의 경우 다음과 같이 Widevine CDM이라는 정보가 나타나게 된다.

![2021-01-03-set-ott-on-xgimi-h1-android-03.png]({{site.baseurl}}/assets/img/post_included/2021-01-03-set-ott-on-xgimi-h1-android-03.png)

`하지만 XGIMI H1 프로젝터의 경우 이 widevine 인증이 되어있지 않는 기기이고, 우리가 보려고 하는 Watcha는 widevine DRM 기술을 사용하기 때문에, 정상적으로 Watcha의 영상을 볼수 없는 것이다.`

추가로, widevine 기술은 현재 구글이 가지고 있고 안드로이드 기기에는 기본적으로 적용이 되어있다는데 왜 안될까 생각해 봤지만 결론은 우리의 XGIMI 친구들이 뭔가 작업(?)을 했다라고 밖에 생각되지 않았다.

## XGIMI H1 프로젝터에 한글 키보드 설정

OTT 시스템으로 사용하는 프로젝터 이므로, 보고 싶은 영상을 검색 하려면 한글 키보드는 필수이다. 하지만 우리 프로젝터에는 영문 키보드밖에 없다. 인터넷에서 검색해보면 안드로이드에서 사용할 수 있는 한글키보드가 굉장히 많지만, 버전이 안맞는 등의 이유로 제대로 설치되지 않는 것들이 대부분이었다. 그러다가 구글에서 제공하는 `Gboard` 라는 키보드가 한글도 지원하며 제일 괜찮다는 것을 알게 되었고, 이를 설치하는 방법으로 프로젝터에 내장된 플레이 스토어는 그대로 둔 채, `새로운 플레이 스토어를 설치 후 Gboard를 다운로드 및 설치`했다. (애플빠로써 플레이 스토어도 따로 설치할 수 있다는 사실이 놀라웠다.) 해당 작업을 할 때, [XGIMI,Touyinger 중국직구 빔프로젝터 공식카페](https://cafe.naver.com/beampow) 의 도움을 많이 받았다.

- 구글 플레이 스토어 : 1.2 버전 설치 (카페 가입 및 "Google play store" 검색 후 다운로드)
- 한글 키보드 : 플레이 스토어 1.2 버전에서 "Gboard" 검색 및 설치
- XGIMI H1 프로젝터 한글 키보드 설정 : `시스템 설정 → 일반 → 입력방법 → Gboard 로 변경`

# 구축 결과 및 애플빠가 바라 본 안드로이드

## 구축결과

- Netflix, Youtube, Naver Sports Live : 안드로이드 TV 자체 앱으로 시청
- Tving, Wavve : KODI 애드온으로 시청
- Watcha : 시청 불가

![2021-01-03-set-ott-on-xgimi-h1-android-04.jpg]({{site.baseurl}}/assets/img/post_included/2021-01-03-set-ott-on-xgimi-h1-android-04.jpg)

## 애플빠가 바라본 안드로이드

애플빠로써, 애플의 주는대로 받는 시스템에 익숙해져 있다 보니, 필요한 것을 스스로 찾아서 다운받고 설치하고 만들어 가는 안드로이드의 시스템이 처음에는 굉장히 불편했다. 찾는 것도 한곳에 딱 모여있는게 아니라 여기서 찾고 없으면 다른데서 찾고 하는것도 그렇고, 기껏 찾았더니 설치도 안되고 하는 것도 불편했다. 하지만 계속 하다보니 자유도가 높아서 내가 만들고 싶은데로 만들 수 있다는 측면이 굉장히 흥미로웠다. 사람들이 왜 안드로이드를 좋아하는지 알 수 있었던 시간이었다.
