---
layout: post
title: Sample blog post
subtitle: Each post also has a subtitle
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [test]
comments: true
---

# 안드로이드 기본 개념

### NDK란

java만 사용하여 필요한 기능과 성능을 모두 만족시키기는 힘들다. 그래서 C나 C++ 언어로 작성된 프로그램을 java에서 사용할 수 있도록 JDK에서 제공하는 것이 JNI(Java Native Interface) 이다.



그리고 NDK는 Developer문서에서도 볼 수 있듯이

The Android NDK is a toolset that lets you implement parts of your app using native-code languages such as C and C++. For certain types of apps, this can help you reuse code libraries written in those languages.



이것을 가능하게 해주는 툴킷이라고 보면 된다.



NDK를 사용하여 얻을 수 있는 장점

\1. 기존에 C로 만들어진 대규모 코드를 JAVA에서 다시 만들 필요없이 재사용이 가능하다.

\2. 시스템 디바이스 접근과 JAVA성능을 넘어선 작업이 필요할때 유용하다.

\3. 속도 및 성능을 향상시킬 수 있다.



이러한 장점때문에 NDK는 주로 영상처리, 게임, 신호처리, 물리 시뮬레이션 등에 사용된다.