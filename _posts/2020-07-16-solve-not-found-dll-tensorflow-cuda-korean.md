---
layout: post
published: true
title: 'CUDA Tensorflow 실행 시 "Could not load dynamic library cudart64_100.dll; dlerror: cudart64_100.dll not found" 오류 해결'
date: '2020-07-16'
tags:
  - CUDA
  - tensorflow
  - 개발환경
---
### 상황

CUDA  설치 후 텐서플로우를 이용해서 코딩을 하고 해당 코드를 실행시킬 때, 다음과 같은 에러 메시지를 볼 때가 있다.

> Could not load dynamic library 'cudart64_100.dll'; dlerror: cudart64_100.dll not found

### 원인

해당 오류는 최신 버전 CUDA 를 설치하고 텐서플로우 1.x 코드를 실행시킬 때 나타나는데, **텐서플로우 1.x에서 사용하는 DLL이 최신 버전 CUDA에는 빠져 있기 때문** 이다. 필자의 경우 초기에 텐서플로우 2.2 버전을 사용하기 위해 최신 버전 CUDA를 설치 했었고, 이 후 1.15 버전으로 환경을 다시 구축해서 1.15 버전의 코드를 실행하려고 했을 때 에러가 발생했다. 또한, 해당 에러가 발생하면 다음의 에러도 함께 발생한다.

```bash
# 총 6개의 DLL이 없다고 나옴

Could not load dynamic library 'cudart64_100.dll'; dlerror: cudart64_100.dll not found
Could not load dynamic library 'cublas64_100.dll'; dlerror: cublas64_100.dll not found
Could not load dynamic library 'cufft64_100.dll'; dlerror: cufft64_100.dll not found
Could not load dynamic library 'curand64_100.dll'; dlerror: curand64_100.dll not found
Could not load dynamic library 'cusolver64_100.dll'; dlerror: cusolver64_100.dll not found
Could not load dynamic library 'cusparse64_100.dll'; dlerror: cusparse64_100.dll not found
```

### 해결

해결방법은 크게 2가지 가 있다.

- CUDA 를 삭제하고 예전 버전으로 재 설치
- CUDA는 현재 버전으로 유지하면서 필요한 DLL만 다운로드

해당 문서에서는 **CUDA는 현재 버전으로 유지하면서 필요한 DLL만 다운로드** 하는 방법을 설명한다.

1. CUDA 설치 폴더에 가서 현재 DLL 들을 확인한다. CUDA의 디폴트 설치 폴더는 다음과 같다.

    > C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin

    ![2020-07-16-solve-not-found-dll-tensorflow-cuda.png]({{site.baseurl}}/assets/img/post_included/2020-07-16-solve-not-found-dll-tensorflow-cuda.png)

    Not found 오류가 발생한 `cudart64_100.dll` 파일은 없고 `cudart64_101.dll` 파일이 보인다.

2. 필요한 DLL 파일을 다운로드 받는다.
    [https://drive.google.com/file/d/1GNx7RYty9wq7TJ8UC0A6Pw_nYGQ1qmep](https://drive.google.com/file/d/1GNx7RYty9wq7TJ8UC0A6Pw_nYGQ1qmep) (해당 파일의 출처는 문서 하단의 '참고'에 표기)    

3. CUDA 설치 폴더 (기본 설정은 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin) 에 다운로드 받은 DLL을 복사한다.

4. 다시 텐서플로우 코드를 실행시키면 정상 동작 하는 것을 확인 할 수 있다.

### 참고

[https://medium.com/@iitbguha/tensorflow-with-gpu-installation-made-easy-659f88c0309b](https://medium.com/@iitbguha/tensorflow-with-gpu-installation-made-easy-659f88c0309b)
