---
title:  "[blog] github blog comments (utterances)"
excerpt: "github 블로그의 댓글 기능을 추가한다."

categories:
  - blog
  - admin
tags:
  - [blog, comments, 댓글기능, utterances]

toc: true
toc_sticky: true
 
date: 2021-09-22 00:00:00 +0900
last_modified_at: 2021-09-22
---


## GitHub Blog 댓글로 Disqus를 사용 

- 얼마 전 github.io 블로그를 개설면서 [Disqus](https://disqus.com/)라는 댓글기능을 많이 사용하고 있어서 아무 문제없이 가입하고 설정 후 사용하게 되었다.
- 두둥.... 하지만 며칠 뒤 부터 댓글 기능 위 아래에.. 광고가 붙기 시작했다.
- 화면의 1/3정도 차지하는 광고들이 너무 지저분하여 대체할수 있는 댓글 기능을 찾기 시작했다.

## 그래서 선택한 것은 utterances 라는 Github App

- 무료이고 광고가 없고 오픈소스라는 장점이 있다.
- 바닐라 타입스크립트를 사용한 경량의 댓글 위젯이다.
- github OAuth flow를 따르기는 하지만 대부분 댓글을 다는 사람도 github 사용자라고 생각되기 때문에 사용하게 되었다.

## utterances 설치 방법

- Github App에서 utterances 설치   
  - [utterances 설치페이지](https://github.com/apps/utterances) 로 이동
  - Install 버튼 클릭
  - 다음 화면으로 대상 repositories를 선택한다. (난 github.io 블로그만 사용할 예정이므로 해당 ps2046.github.io를 선택)
  - 잘 선택했다면 하단의 Install을 눌러 진행하면 된다.

## utterances 설정 (configuration) 방법

- configuration > Repository
  - 내가 댓글 저장소로 사용할 repo를 등록해준다. (저장소는 직접 생성해준다.)
  - repo: 본인계정/저장소명 형태로 등록하면 된다.   

- configuration > Blog Post ↔️ Issue Mapping

  - blog 이슈와 posts 와의 맵핑 방법을 선택한다.
    * Issue title contains page pathname
    * Issue title contains page URL
    * Issue title contains page title
    * Issue title contains page og:title
    * Specific issue number
    * Issue title contains specific term

  - 저는 기본으로 첫번째 선택! page pathname 을 이슈 타이틀에 포함되도록 했다.

- configuration > Issue Label
  - optional로 label이 필요할 경우 세팅

- configuration > Theme
  - 테마는 자신의 블로그에 맞게 선택하면 될거 같다.

- configuration > Enable Utterances
  - 모두 설정을 입력하고 선택했다면 아래와 같이 스크립트가 생성이 된다.
    ```javascript
    <script src="https://utteranc.es/client.js"
        repo="ps2046/ps2046-github-io-comments"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
    </script>
    ```

## utterances 페이지에 설정 

- "_layouts/post.html" 에 위에서 나온 스크립트를 넣어주면 된다.