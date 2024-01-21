---
layout: post
title: "Jekyll로 블로그 만들기"
keywords: "Jekyll 사용법, Jekyll로 블로그 만들기, jekyll, jekyll blog, jekyll devlog"
date: 2022-02-15 20:49:00 +0900
background: '/img/posts/2022-02-15-blog.jpg'
categories: etc
---

# Jekyll로 Github Pages 블로그 만들기

------------------------------

<br/>

Github pages와 Jekyll을 이용하면 "내 이름.github.io"가 주소인 블로그를 만들고 관리할 수 있다. 이 블로그 역시 Jekyll을 사용하여 만들어졌다.

- (깃허브 페이지 : <https://pages.github.com/>) 
- (Jekyll 사이트 : <https://jekyllrb-ko.github.io/>)

<br/>

jekyll은 Ruby로 만들어진 정적 사이트 생성기이다. 

Ruby 문법을 몰라도 Jekyll 사이트에 Jekyll 사용 방법이 쉽게 적혀있어서 쉽게 블로그를 만들 수 있다. (한글 번역도 꽤 잘 되어있다.) 

아래 내용은 윈도우10 환경에서 진행한 것이다. 


<br/>

## Jekyll 설치하기

--------------------------------

<br/>

1.  <a href="https://jekyllrb-ko.github.io/docs/installation/windows/" target="_blank">"Jekyll 설치하기"</a>  페이지에 들어가서 설명을 읽고 Ruby와 Jekyll을 설치한다.
<br/>

2.  Ruby 설치 가이드 중 '설치 마법사의 마지막 단계에서 ridk install 절차를 수행하세요.'
라는 말이 있다. 하지만, Ruby 설치 마법사 화면에서 마지막 단계에서 'ridk install' 옵션이 이미 체크가 되어있으니 확인 후 넘어가면 된다.
<br/>

3. 마지막으로 bundler를 설치한다. 


<br/>

## 블로그 만들기

---------------------------------

<br/>

1. <a href="https://jekyllrb-ko.github.io/docs/" target="_blank">"새 Jekyll사이트 생성하기."</a>를 참고하여 원하는 디렉토리에 새 프로젝트를 생성한다.

        $jekyll new myblog

2. 로컬호스트(http://localhost:4000)에서 생성된 사이트를 확인할 수 있다.

        $bundle exec jekyll serve

3. 지킬 블로그 테마를 이용할 수도 있다.(강력히 권장) 이 블로그의 테마 : <a href="https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll" target="_blank">'clean-blog-jekyll'</a>

4. 위 깃허브 주소에 접속 후, Readme에서 "Using core files" 방법을 따라한다.

5. 내 깃허브에서 repository를 생성한다. (반드시 깃허브 페이지 : <https://pages.github.com/> 에서 설명하는 대로 repository를 만들 것.)

6. 테마 파일을 clone한다.

        $git clone https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll.git

7. _config.yml을 수정하여 나만의 블로그를 만든다. ( <a href="https://github.com/StartBootstrap/startbootstrap-clean-blog-jekyll" target="_blank">'clean-blog-jekyll'</a> 에서 가이드 참고)

8. 테마 파일 연결을 해제한다.

        $git remote rm origin

9. 커밋

        git add .
        git commit -m "commit message"

10. 푸쉬

        git branch -M main
        git remote add origin <내 깃허브 repository>
        git push origin main
 
이제, "https://<사용자명>.github.io"로 접속하면 블로그를 확인할 수 있다. (몇 분 걸릴 수 있다.) 

