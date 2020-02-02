---
layout: post
title: Github pages 작성하기
subtitle: 윈도우에서 Github pages를 사용하기 위한 설정
tags: [github, github-pages, jekyll, blog, visual studio code]
image: /assets/images/2020-01-19-VSCode-Github-make-pages/gitlogo.png
comments: true
---

Github pages를 이용하여 블로그를 운영하기로 결정한 후 가장 먼저 한 것은 Github Desktop 설치와 Visual Studio Code(이후 VS Code로 표기) 설치이다.
Github 계정 및 repository 생성 등은 이미 준비되어 있는 상태였고, 처음엔 Github 웹에서 수정하던 것을 제대로 작업 환경을 구축해야 겠다는 생각에 작업을 진행했다. Github Desktop은 Github에서 제공하는 도구로 작성한 마크다운 페이지를 Github repository에 손쉽게 push할 수 있다. 사용해보니 GUI 프로그램으로 되어 있어서 매우 직관적이고 사용하기가 쉬었다. Visual Studio Code는 마크다운 편집기로 문서를 작성하기에 편리하다.

## Visual Stdudio Code 설치

Visual Studio Code는 무료로 사용이 가능하다. [MS 공식 사이트](https://code.visualstudio.com/)에서 다운로드 후 설치한다. 설치 과정은 매우 평범하여 설명을 생략한다.

## Git 설치

VS Code에서 포스트를 작성하고 Github Desktop을 사용하여 commit, push를 할 수도 있지만, VS Code 하나로도 모든 과정이 가능하기 때문에 필요한 경우만 Github Desktop을 사용하고 주로 VS Code를 사용하기로 하였다.
우선 VSCode에서 Git을 사용하려면 로컬에 Git을 설치해야 한다. [Git 공식 사이트](https://gitforwindows.org/)에서 Git for Windows를 다운로드하여 설치한다. 설치 방법은 많은 사이트에서 소개하고 있기에 생략한다. 단, Defalt Editor 선택 화면에서 "Use Visual Studio Code as Git's default editor"를 선택한다.

![Default Editor 선택](/../../assets/images/2020-01-19-VSCode-Github-make-pages/2020-01-19-VSCode-Github-make-pages_2020-01-20-00-46-16.png)

## VS Code에서 Git 설정

VS Code를 실행한 후 "Source Control" 메뉴를 클릭한 후 "레파지토리 초기화" 버튼을 클릭하여 폴더를 선택하면 버전관리가 시작된다.

![레파지토리 초기화 버튼](/../../assets/images/2020-01-19-VSCode-Github-make-pages/2020-01-19-VSCode-Github-make-pages_2020-02-03-01-32-28.png)

이제 Git의 기능을 이용할 수 있게 되었다.
Workspace의 파일을 추가 및 편집 후 소스제어 화면으로 이동하면 변경된 리스트를 보여주는데, + 표시를 클릭하면 해당 파일이 "stage changes"로 변경된다. "CHANGES"의 +를 클릭하면 변경된 모든 파일을 한번에 적용할 수 있다.

![Source Control: GIT](/../../assets/images/2020-01-19-VSCode-Github-make-pages/2020-01-19-VSCode-Github-make-pages_2020-02-03-01-44-01.png)

이후 상단에 Commit(체크) 버튼을 클릭하면 변경 파일들이 Commit되고, "More Actions"에서 Push 버튼을 클릭하면 원격 레파지토리에 push된다.


## 유용한 Extension
Visual Stduio Code는 매우 다양한 Extension을 사용할 수 있다는 것이 큰 장점 중 하나이다. [Visual Studio Code를 Markdown Editor로 사용하기](https://thecodinglog.github.io/tool/markdown/2018/07/25/markdown-editor.html)에서 마크다운 문서를 작성할 때 유용한 실시간 미리보기, 단축키로 텍스트 모양 변경, 이미지 저장 팁을 제공하고 있어 참고하여 설치하였다.
