---
layout: post
title: "Jekyll로 블로그 만들기"
keywords: "Jekyll 사용법, Jekyll로 블로그 만들기, jekyll, jekyll blog, jekyll devlog"
date: 2022-02-15 20:49:00 +0900
background: '/img/posts/2022-02-15-blog.jpg'
categories: etc
---

# Jekyll로 블로그 만들기.
"<내 이름>.github.io"가 주소인 나만의 블로그를 만들고 싶었던 적이 있으셨나요? 이번 포스트는 github pages와 jekyll을 이용해서 정적 웹사이트를 만드는 방법입니다. 지금 보고 계신 블로그가 이 방법으로 만들어졌으니, 따라해보고 싶으신 분들은 아래 방법을 참고하시면 쉽게 만들 수 있습니다.

- (깃허브페이지 : <https://pages.github.com/>) 
- (Jekyll 공식 문서 : <https://jekyllrb-ko.github.io/>)
  
-----------------------------

jekyll은 Ruby라는 언어로 된 정적 사이트 생성기이다. 

하지만 Ruby 문법을 몰라도 Jekyll사이트에서 설명을 참고하면 쉽게 이용할 수 있다. (한글 번역도 잘 되어있다.) 

Jekyll 공식 사이트에서 jekyll이 어떤 식으로 동작하는 지 자세히 알 수 있다.

해당 내용은  윈도우10 환경에서 진행한 것이다. 윈도우 10 환경에서는 윈도우 명령 프롬프트(cmd)대신 <a href="https://cmder.net/" target="_blank">Cmder</a>를 설치해서 사용하는 것을 추천한다. (리눅스 명령어를 사용할 수 있어 편하다.)

--------------------------------

## Jekyll 설치하기

1.  <a href="https://jekyllrb-ko.github.io/docs/installation/windows/" target="_blank">"Jekyll 설치하기"</a>  페이지에 들어가서 설명을 읽어보며 Ruby와 Jekyll을 설치한다.
2.  설치 가이드에 '설치 마법사의 마지막 단계에서 ridk install 절차를 수행하세요.'
라는 말이 있다. 설치 마법사 화면에서 '다음'버튼을 누르다가 마지막 단계에서 'ridk install' 옵션이 이미 체크가 되어있으니 그냥 넘어가면 된다.
3. 마지막으로 bundler까지 깔아준다. 

## 프로젝트 생성하기

1. <a href="https://jekyllrb-ko.github.io/docs/" target="_blank">"새 Jekyll사이트 생성하기."</a>를 참고하여 적절한 디렉토리 내에 새 프로젝트를 생성한다.

        $jekyll new myblog

2. 로컬호스트(http://localhost:4000)에서 생성된 사이트를 확인한다.

        $bundle exec jekyll serve

3. 지킬 블로그 테마를 이용한다. <a href="https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll" target="_blank">'clean-blog-jekyll'</a>

4. 위 깃허브 주소에 접속 후, 가이드에서 "Using core files" 방법 따라하기.

5. 내 깃허브에서 repository 생성.

6. 테마 파일 clone하기.

        $git clone https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll.git

7. _config.yml 수정 ( <a href="https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll" target="_blank">'clean-blog-jekyll'</a> 에서 가이드 참고)

8. 테마 파일 연결 해제

        $git remote rm origin

9. 커밋

        git add .
        git commit -m "commit message"

10. 푸쉬

        git branch -M main
        git remote add origin <내 깃허브 repository>
        git push origin main
 
1분 정도 기다린 후 "https://<사용자명>.github.io"로 접속하면 jekyll 테마를 통해 만든 사이트를 확인할 수 있다. 

