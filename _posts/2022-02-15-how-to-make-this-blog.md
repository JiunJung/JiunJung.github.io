---
layout: post
title: "Jekyll로 블로그 만들기"
keywords: "Jekyll 사용법, Jekyll로 블로그 만들기, jekyll, jekyll blog, jekyll devlog"
date: 2022-02-15 20:49:00 +0900
background: '/img/posts/2022-02-15-blog.jpg'
categories: DevJiun
---

# Jekyll로 블로그 만들기. | Jekyll 사용법
내가 웹 개발에 막 관심이 가기 시작했을 때 "내 이름.github.io"가 주소인 내 블로그를 만들고 싶었다. 이번 포스트는 github pages와 jekyll을 이용해서 정적 웹사이트를 만드는 방법이다.
- (깃허브페이지 : <https://pages.github.com/>) 
- (Jekyll 공식 문서 : <https://jekyllrb-ko.github.io/>)

jekyll은 Ruby라는 언어로 된 정적 사이트 생성기이다. 하지만 Ruby 문법을 몰라도 Jekyll사이트에서 설명을 참고하면 쉽게 이용할 수 있다. (한글 번역도 잘 되어있다.) 
Jekyll 공식 사이트에서 jekyll이 어떤 식으로 동작하는 지 자세히 알 수 있다.

나는 윈도우10 환경에서 진행하였다. 윈도우 10 환경에서는 윈도우 명령 프롬프트(cmd)대신 <a href="https://cmder.net/" target="_blank">Cmder</a>를 설치해서 사용하는 것을 추천한다. (맥의 터미널처럼 쓸 수 있고 편하다.)

먼저 <a href="https://jekyllrb-ko.github.io/docs/installation/windows/" target="_blank">"Jekyll 설치하기"</a> 이 페이지에 들어가서 설명을 읽어보며 Ruby를 깔고 그 다음 Jekyll을 설치한다. 설명 중에 '설치 마법사의 마지막 단계에서 ridk install 절차를 수행하세요.'
라는 말이 있는 데 설치하는 과정에서 '다음'버튼을 누르다보면 이미 체크가 되어있는 것을 확인할 수 있다. 따로 뭐 해줄 건 없다. 그리고 설명대로 bundler까지 깔아준다. 

그 다음 단계로, <a href="https://jekyllrb-ko.github.io/docs/" target="_blank">"새 Jekyll사이트 생성하기."</a>를 참고하여 적절한 디렉토리 내에 새 프로젝트를 생성한다. 
Cmder(프롬프트 창)에 "jekyll new myblog"를 하는 순간 myblog폴더 내에 gemgile, _config.yml등 많은 파일들이 생성된다. 이대로 "bundle exec jekyll serve" 명령어를 치면 "http://localhost:4000"에서 생성된 사이트를 확인할 수 있다. 
이 때 생성되는 사이트는 지킬 기본 테마로 만들어진 사이트이다. 사이트를 살펴보면 _config.yml은 어떻게 수정해야하고 post는 어떻게 쓰는 지에 대한 설명이 잘 쓰여있다. 
이대로 깃허브에 올려 블로그로 쓸 수도 있지만 사이트가 너무 안 예쁘다.  

구글에 Jekyll theme best를 검색해보면 사람들이 많이 쓰는 괜찮은 테마를 찾을 수 있다. 나의 경우 <a href="https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll" target="_blank">'clean-blog-jekyll'</a>을 이용하였다.
README.md에 사용법이 아주 자세하게 나와있다. README.md에는 이 테마를 사용하는 두가지 방법으로 Using Rubygems와 Using core files가 있는데, Using core files 방법을 따라하는 것이 좋다. 나는 처음에 Using Rubygems 방법을 따라했는데,
github pages에서 gem "jekyll-theme-clean-blog"을 지원하지 않는지 계속 github-pages failure가 뜨면서 실패했다. 
github repository의 name은 사용자명.github.io로 하고 깃허브 pro가 아니라면 public으로 해야한다.

repository 생성 후, Cmder(프롬프트 창)에서 "git clone https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll.git" 으로 테마 파일을 clone하고 README.md의 설명대로 _config.yml을 수정한다.
그리고 "bundle exec jekyll serve" 명령어를 통해서 "http://localhost:4000"를 확인한다. (내가 원하는 사이트가 잘 만들어졌는지 확인한다.)
그리고 "git remote rm origin" 명령으로 테마 파일 연결을 해제한다. (자신의 repository에 연결해야하므로) 그 다음 "git add ." 명령으로 커밋할 파일을 올린 다음, "git commit -m "<i>커밋한 내용 설명</i>""으로 커밋한다. 
git branch -M main으로 브랜치 이름을 main으로 바꿔주고,<small>(인종차별적 요인이 있다는 이유로 기존의 브랜치명인 Master 대신 Main을 쓴다.)</small> "git remote add origin <small><i>자신의 깃허브 repository</i></small>" 으로 원격 저장소로 자신의 깃허브 repository를
등록하고 "git push origin main"으로 푸시한다. 

1분 정도 기다린 후 사용자명.github.io로 접속하면 jekyll 테마를 통해 만든 사이트를 확인할 수 있다. 

