---
layout: post
title: VS Code로 Github pages 작성하기
subtitle: 윈도우에서 Github pages를 사용하기 위한 설정
tags: [Development, github, github-pages, jekyll, blog]
image: /img/avatar-icon.png
comments: true
---

Github pages를 이용하여 블로그를 운영하기로 마음을 먹고 가장 먼저 한 것은 Github Desktop 설치와 Visual Studio Code 설치이다.
Github 계정 및 repository 생성 등은 이미 준비되어 있는 것으로 보고 생략한다. Github Desktop은 Github에서 제공하는 도구로 작성한 마크다운 페이지를 Github repository에 손쉽게 push할 수 있다. Visual Studio Code는 마크다운 문서를 작성하는 도구로 사용한다.

## Git 설치

VS Code에서 포스트를 작성하고 Github Desktop을 사용하여 commit, push를 할 수도 있지만, VS Code 하나로도 모든 과정이 가능하기 때문에 필요한 경우만 Github Desktop을 사용하고 주로 VS Code를 사용하기로 하였다.
우선 VSCode에서 Git을 사용하려면 로컬에 Git을 설치해야 한다. [Git 공식 사이트](https://gitforwindows.org/)에서 Git for Windows를 다운로드하여 설치한다. 설치 방법은 많은 사이트에서 소개하고 있기에 생략한다. 단, ![Default Editor 선택](/../../assets/images/2020-01-19-VSCode-Github-make-pages/2020-01-19-VSCode-Github-make-pages_2020-01-20-00-46-16.png)화면에서 "Use Visual Studio Code as Git's default editor"를 선택한다.

## Visual Stdudio Code 설정

### 

### 유용한 Extension
Visual Stduio Code는 매우 다양한 Extension을 사용할 수 있다는 것이 큰 장점 중 하나이다. [Visual Studio Code를 Markdown Editor로 사용하기](https://thecodinglog.github.io/tool/markdown/2018/07/25/markdown-editor.html)에서 마크다운 문서를 작성할 때 유용한 실시간 미리보기, 단축키로 텍스트 모양 변경, 이미지 저장 팁을 제공하고 있어 참고하여 설치하였다.

