---
layout: post
title: 로컬에서 Github Pages 생성하기
subtitle: 로컬에서 Ruby와 Jekyll을 사용하여 마크다운을 github pages로 생성하기
tags: [Github Pages, Markdown, Ruby, Jekyll]
image: /assets/images/2020-03-20-build-jekyll-markdown/jekyll.png
comments: true
---

Github Pages에 Jekyll 테마를 이용하여 포스팅을 하던 도중 최근에 보안 이슈로 인해 Ruby, nokogiri를 업데이트를 해야만 했습니다. 그러나 업데이트 후 포스팅 문서의 빌드가 실패했다는 메일을 지속적으로 받게 되었고, 쉽게 해결이 되지 않았었습니다.

제공되는 힌트는 매우 부족해서 무엇인 문제인지 찾기가 어려웠습니다. 사실 그보다도 포스팅을 할 때마다 마크다운 문서를 Github에 push한 후에야 확인이 가능해서 수정이 잦았던 문제가 있어 고민하던 중에 이번 기회에 Jekyll 빌드를 통해서 로컬에서 마크다운 문서를 미리 확인하고 최종 버전을 push하기로 결정했습니다. 찾아보니 Jekyll serve를 통해서 빌드 에러 메시지를 확인할 수 있어서 문제 해결에도 도움이 될 수 있다고 합니다.

## Ruby with Devkit 설치하기

[RubyInstaller](https://rubyinstaller.org/downloads/) 사이트에서 DEVKIT이 포함된 버전을 선택하고, 안정화 버전을 다운로드합니다. 2020년 3월 현재는 Ruby+Devkit 2.6.5-1 (x64) 버전을 권장하고 있습니다. 다운로드가 완료되면 기본 설정으로 설치를 진행합니다.

## Jekyll 설치하기

Start Command Prompt with Ruby를 실행하여 아래와 같이 Jekyll을 설치할 폴더로 이동 후 Jekyll을 설치합니다. Jekyll 설치가 완료되면 설치가 제대로 되었는지 확인하기 위해 아래 명령어를 실행합니다.

```ruby
> mkdir jekyll_site
> cd jekyll_site
> gem install jekyll bundler
> jekyll -v
```

## 사이트 생성하기

Jekyll 설치가 완료되면 아래의 명령어로 새로운 사이트를 생성합니다. 마지막에 './'는 현재 경로를 의미합니다. 다른 경로를 지정할 수 있습니다.

```ruby
> jekyll new ./
> bundle install
```

생성이 완료되면 아래의 명령어로 서버를 실행한 후 브라우저에서 http://127.0.0.1:4000로 접속하여 사이트를 확인합니다.

```ruby
> bundle exec jekyll serve
```

## 로컬 빌드를 통한 문제 해결

결과적으로 이 포스팅을 통해서 Jekyll dependency 문제를 해결할 수 있었고, 또 하나 간과하고 있었던 매우 큰 문제점을 찾을 수 있었습니다. 정식 포스팅 이전에 임시로 commit 했던 문서가 계속해서 빌드를 실패했고, 그로 인해 다른 포스팅의 빌드를 방해하여 아무리 작성해서 갱신이 안되고 있다는 것을 알게되었습니다.

## Reference

* ['jekyll serve' 문제 해결하기](https://ychae-leah.tistory.com/15)
* [Jekyll을 이용해 GitHub에 블로그 만들기](https://jetalog.net/86)
