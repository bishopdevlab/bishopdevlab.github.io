---
layout: post
title: Ruby update에 따른 Github Pages 업데이트
subtitle: Ruby 업데이트 후 로컬에서의 Jekyll github page를 실행시키기
tags: [Github Pages, Markdown, Ruby, Jekyll]
image: /assets/images/2022-04-05-update-jekyll-page/ruby_jekyll.png
comments: true
---

회사 일로 너무 바쁜 2년을 보내다가 다시 블로그에 글을 작성하려고 로컬에 Ruby 최신버전을 설치했습니다. Github repository에 글을 push하면 작성된 페이지를 볼 수 있는데까지 대략 5분정도 걸리기 때문에 로컬에 실행환경을 구축하는 것이 더 효율적입니다.
RubyInstaller 최신버전을 받아 설치 후 로컬의 Github page repository에서 Jeykll을 실행하는데 몇가지 에러가 발생됩니다. 본 글은 이를 해결하는 과정을 설명합니다.

## Ruby with Devkit 설치하기

[RubyInstaller](https://rubyinstaller.org/downloads/) 사이트에서 DEVKIT이 포함된 버전을 선택하고, 안정화 버전을 다운로드합니다. 2022년 4월 현재는 Ruby+Devkit 3.1.1-1 (x64) 버전을 권장하고 있습니다. 다운로드가 완료되면 기본 설정으로 설치를 진행합니다.

## Jekyll 실행하기

VS Code에서 터미널을 실행하여 clone되어 있는 repository 경로로 이동합니다. bundle exec jekyll serve 명령어로 서버를 실행합니다.

```ruby
> cd xxxx.github.io
> bundle exec jekyll serve
```

## Gemfile.lock 생성하기

```ruby
Could not find concurrent-ruby-1.1.5 in any of the sources
Run `bundle install` to install missing gems.
```

서버 실행 후 에러가 발생된다면 Gemfile.lock 파일을 삭제하여 버전 정보를 제거한 후 다시 생성합니다.

```ruby
> bundle install
```

Gemfile.lock 파일이 만들어지지 않는 경우 Gemfile에 문제가 있는 경우입니다. 저의 경우는 아래처럼 '197'이 정확하게 어떤 의미인지는 모르겠지만, 제거하니 Gemfile.lock 파일이 만들어졌습니다.
문제가 해결되었으니 다시 서버 실행을 시도합니다.

Gemfile

```ruby
# gem "github-pages", '197', group: :jekyll_plugins
gem "github-pages", group: :jekyll_plugins
```

```ruby
> bundle exec jekyll serve
```

## Timezone 문제

서버 실행 후 아래와 같이 timezone 에러가 발생된다면 2가지 설정을 확인합니다.

```ruby
Configuration file: D:/GitHub/bishopdevlab.github.io/_config.yml
jekyll 3.9.0 | Error:  No source of timezone data could be found.
Please refer to https://tzinfo.github.io/datasourcenotfound for help resolving this error.
```

첫번째는 Gemfile에 아래와 같이 timezone 정보가 추가되어 있는지 확인합니다. 특히 64bit 머신의 경우 x64_mingw가 포함되어야 합니다.

```ruby
gem 'tzinfo'
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]
```

두번째는 _config.yml 파일에서 timezone 설정 정보가 있다면 주석 처리 합니다.

```ruby
# timezone: "Asia/Seoul"
```

다시 서버 실행을 시도합니다.

```ruby
> bundle exec jekyll serve
```

## cannot load such file -- Webrick (LoadError)

아래의 에러가 발생되는 경우는 Webrick이 필요하다는 의미입니다. Ruby 3.0 버전부터 gem에 webrick 이 포함되지 않아서 발생된 문제입니다.

```ruby
C:/Ruby31-x64/lib/ruby/gems/3.1.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
```

따라서 bundle add webrick 명령어로 webrick을 추가해줍니다.

```ruby
> bundle add webrick
```

다시 서버 실행을 시도합니다.

```ruby
> bundle exec jekyll serve
```

Wdm 경고가 발생되는 경우 Gemfile에 아래의 내용을 추가한 후 다시 install합니다.

Gemfile

```ruby
gem 'wdm', '~> 0.1.1', :install_if => Gem.win_platform?
```

```ruby
> bundle install
```

서버를 실행 했을 때 아래처럼 메시지가 뜨면 정상적으로 실행이 된것입니다. 서버 주소로 접속하면 page가 실행되는 것을 확인할 수 있습니다.

```ruby
 Auto-regeneration: enabled for 'xxxx.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

## Reference

* [Github Pages 04. 타임존 관리](https://jennysgap.tistory.com/entry/Github-Pages-04-%ED%83%80%EC%9E%84%EC%A1%B4-%EA%B4%80%EB%A6%AC)
* [jekyll 실행 시킬 때 `require': cannot load such file -- webrick (LoadError) 오류가 난다면 bundle add webrick](https://junho85.pe.kr/1850)
