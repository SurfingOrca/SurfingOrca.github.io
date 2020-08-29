---
title: Minimal Mistakes로 블로그 제작 후 수정사항 실시간 확인하는 방법
excerpt: "Ubuntu로 Ruby설치 후 Jekyll 서버 재시작 하기!"

toc: true
toc_label: "Table of Contents"
toc_sticky: true
categories:
  - Study
tags:
  - blog
  - Ruby
  - Ubuntu
last_modified_at: 2020-08-29
---

**孤軍奮鬪 (고군분투) :** (1) 운동경기나 싸움에서 혼자서 많은 수의 적들을 상대하여 힘들게 싸움.  
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; **<U>(2) 남의 도움을 받지 아니하고 힘에 벅찬 일을 잘해 나가는 것을 비유적으로 이르는 말.</U>**
{: .notice--success}

> **Aloha~!**

## 들어가기 전:

- 다른 OS는 잘 모르고 Windows OS만 사용해보신 ~~(저와 같은)~~ 분들에게 도움이 되길 바랍니다.
- 필요한 준비는 다음과 같습니다.
    - git 설치
    - github 계정 생성
    - Minimal Mistakes 혹은 Jekyll Theme으로 블로그 셋업 완료
        - 아주 간단하게만 셋업되어 있어도 좋습니다.

<br>

## 1. Introduction

멋진 친구로부터 손쉽게 github에 블로그를 만들 수 있다는 말을 듣고 움직였습니다.  
(Thank you, [Sean](https://github.com/Sean-Parkk))  
&nbsp;


Jekyll 테마 중 Minimal mistakes를 이용하여 블로그를 생성하는 것은 상대적으로 쉬웠습니다.
- Jekyll에 대해서 알고 싶다면 [이곳](http://t-robotics.blogspot.com/2016/04/jekyll.html#.X0b8tcgzZPY)과 [이곳](https://jekyllrb.com/docs/)을 방문해보아요~  
&nbsp;


간단하게 이야기하면
1. Github에 블로그(혹은 사이트)를 위한 Repository를 생성
2. Minimal Mistakes의 Repository에서 Fork
3. 필요한 부분만 복사/붙여넣기

이렇게 하면 끝! ~~(이 아닌 시작이라는 게 함정)~~  
&nbsp;


이렇게 블로그를 셋업하는 방법은 여러 블로그에 소개되어 있습니다.
제가 참고한 블로그들은 아래 블로그들입니다. 링크를 타고 넘어가세요~
- [Jekyll 블로그 테마 적용하기 (minimal-mistakes)](https://junhobaik.github.io/jekyll-apply-theme/)
- [JEKYLL, GITHUB.IO, MINIMAL MISTAKES 블로그 만들기, 목차 한글링크 버그](https://hahafamilia.github.io/howto/jekyll-github-mistakes-blog/)
- [Jekyll, Github Pages, Minimal Mistakes 로 시작하는 깃허브 블로그 튜토리얼](https://green4469.github.io/blog/start_github_blog/)

<br>

## 2. Then, why am I writing this post?

셋업하면서 가장 불편했던 부분은 내가 수정한 내용을 실시간으로 확인할 수 없다는 점이었습니다.

Minimal Mistakes의 공식 소개 사이트에는 다음과 같이 나와 있습니다.

**Note:** for technical reasons, _config.yml is NOT reloaded automatically when used with jekyll serve. If you make any changes to this file, please restart the server process for them to be applied.
{: .notice--warning}

> 야매 번역: **"기술적인 이유로 블로그를 수정해도 바로 적용되지 않아요! Jekyll 서버를 다시 시작해야 바로 확인할 수 있어요"**

내가 변경한 부분을 바로 볼 수 없다니. 제대로 고쳐졌는지, 글은 잘 올라갔는지, 수정한 테마가 잘 어울리는지 등을 바로 볼 수 없으면 언제 돌아와서 확인한단 말인가??..  
&nbsp;


그래서 꼭 해결하고 싶었고 **고군분투**.. 했고 성공했습니다.

다만 성공하기 위해 참고했던 사이트, 블로그, 코멘트가 셀 수 없을 정도입니다.

사실 방법은 간단합니다. 그 방법이 여기저기 퍼져있어서 한땀 한땀 모아서 엮는 게 힘들었을 뿐.

***그래서 한곳에 모아 정리했습니다.***

<br>

## 3. So, how to do it?

### 1. Ruby 설치

Ruby를 설치하는 이유는 Jekyll이 Ruby로 개발되었기 때문입니다. Jekyll 서버를 다시 시작하려면 Ruby가 설치되어 있어야 가능하죠. (Minimal Mistakes도 Jekyll Theme 중 하나입니다)

Linux OS에서 Ruby를 설치할 수 있는데 그래서 Ubuntu 설치가 필요합니다. Ubuntu는 Linux OS를 Windows에서 사용할 수 있도록 도와주는 프로그램입니다.  
&nbsp;


1. Ubuntu 설치에 앞서 환경 설정을 변경해줘야 합니다. Windows에서 Linux OS를 사용하기 위한 변경이라고 이해하면 될 것 같아요.
    - 제어판 → 프로그램 → 프로그램 및 기능 → Windows 기능 켜기/끄기 → Linux용 Windows 하위 시스템 선택 → 재부팅

        ![Image_1]({{ site.url }}{{ site.baseurl }}/assets/images/2020-08-29-blog_setup/blog_setup_01.png)
&nbsp;  
&nbsp;

2. 재부팅을 하셨으면 Microsoft Store에서 Ubuntu를 설치하고 실행해줍시다.

    ![Image_2]({{ site.url }}{{ site.baseurl }}/assets/images/2020-08-29-blog_setup/blog_setup_02.png)
&nbsp;  
&nbsp;

3. 설치가 완료되면 Ubuntu를 실행합시다.
    - 끝난 줄 알았지만 조금 더 기다려봅시다.

      ![Image_3]({{ site.url }}{{ site.baseurl }}/assets/images/2020-08-29-blog_setup/blog_setup_03.png)
&nbsp;  
&nbsp;

4. 설치가 완료되면 `UNIX username`을 입력하라고 나옵니다. 전 surfingorca로 정했어요.  
&nbsp;

5. 이후 `password`를 입력하고 한 번 더 확인해주면 설치가 완료됩니다.
    - `Password` 입력 시 안 보여도 당황하지 마세요. 안 보이는 상태로 잘 입력되고 있습니다.
    - 이후로도 비번 입력은 늘 안 보이는 상태로 진행합니다.
&nbsp;  
&nbsp;

6. Ubuntu 터미널에 다음 명령어들을 입력하여 RVM을 설치합시다.
($ 이후 명령어를 입력하시면 됩니다)

    ```
    $ sudo apt-get install software-properties-common
    $ sudo apt-add-repository -y ppa:rael-gc/rvm
    $ sudo apt-get update
    $ sudo apt-get install rvm
    ```

    - Ruby를 바로 설치하기보다 RVM(Ruby Version Manager)을 통해 설치면 Ruby를 관리하는데 더 편리하다는 글을 봐서 그렇게 했습니다. (아직 왜 그런지는 공부하지 않은 부분이라 넘어가겠습니다. 지금은 몰라도 블로그를 셋업하는데 지장이 없습니다)
    - 복사/붙여넣기 하실 분들은 단축키가 달라도 당황하지 마세요.
    위 코드를 `Ctrl + c` 하시고 Ubuntu 터미널에선 `마우스 오른쪽 클릭` 혹은 `Shift + Insert` 를 하시면 돼요.
    - RVM 설치는 조금 오래 걸리는 편이니 물 한잔하고 오세요~
&nbsp;  
&nbsp;

7. 이후 RVM을 통해 Ruby를 설치합시다.

    ```
    $ echo 'source "/etc/profile.d/rvm.sh"' >> ~/.bashrc
    $ rvm install ruby
    ```

    - 첫 번째 코드는 터미널에서 `Run command as login shell` 설정을 선택하게 합니다.
    - 그 이후에야 비로소 루비를 설치할 수 있습니다.
        - 설치에 어려움이 있거나 자세한 설명을 보고 싶다면 [링크](https://github.com/rvm/ubuntu_rvm)를 클릭하세요~

<br>

### 2. Jekyll Server 활성화

이렇게 루비 설치가 끝났습니다. 이제 Jekyll과 기타 Ruby 의존성 패키지들을 설치합시다.  
&nbsp;

1. 먼저 Github 블로그와 연결된 폴더로 이동해야 합니다.

    ```
    $ cd /mnt/c/[폴더 경로]
    ```

    - 이유는 Gemfile이 있는 곳에서 설치가 이뤄져야 합니다. Minimal Mistakes를 제대로 가져왔다면 Gemfile이 폴더에 있을 겁니다. 없다면 Minimal Mistakes Repository에서 가져옵시다.
    - cd는 Change Directory를 의미합니다. 이동할 때는 꼭 한 줄에 전체 경로를 입력합시다.
&nbsp;  
&nbsp;

2. 이동한 폴더에서 나머지 필요한 설치를 진행합시다.

    ```
    $ bundle install
    ```

    - 위 코드를 통해 필요한 패키지(Jekyll 포함)를 설치합니다.
&nbsp;  
&nbsp;

3. 이제 설치는 모두 끝났습니다. 다음 코드를 실행하기 전에 컴퓨터를 한 번 부팅해줍시다
    - 제 경우 부팅을 해야 에러 없이 다음 코드가 진행되었습니다.
&nbsp;  
&nbsp;

4. 부팅 후 다음 코드를 실행하여 서버가 잘 연동되는지 확인해봅시다.

    ```
    $ Bundle exec jekyll serve --no-watch
    ```

    - 혹 에러를 만나게 되면 마지막 관문이라 생각하고 침착하게 다음 코드를 실행합니다.

        ```
        $ sudo chown -R [your username] /mnt/c/[블로그 폴더 경로]
        ```

        - 그 후 부팅 후 위 코드를 실행하세요. 저는 부팅 안 하고 실행하니 똑같은 에러를 만났어요 ㅎㅎ
        - 관련하여 stack overflow에 올라온 [질문과 답](https://stackoverflow.com/questions/57243299/jekyll-operation-not-permitted-apply2files)을 참고하세요.
&nbsp;  
&nbsp;

5. 잘 실행되었다면 아래 그림과 같이 접속 가능한 URL을 볼 수 있습니다.

    ![Image_4]({{ site.url }}{{ site.baseurl }}/assets/images/2020-08-29-blog_setup/blog_setup_04.png)

    - 웹 브라우저에서 [http://127.0.0.1:4000](http://127.0.0.1:4000) 을 여시면 블로그를 바로 확인하실 수 있습니다.

<br>

## 4. Great. Now what?

이제 블로그를 수정한 뒤 바로 확인하고 싶으면 서버 접속을 끊고 다시 재접속하면 바로 확인할 수 있습니다.

![Image_5]({{ site.url }}{{ site.baseurl }}/assets/images/2020-08-29-blog_setup/blog_setup_05.png)

- `Ctrl + c` 를 누르면 서버 접속을 끊을 수 있습니다.
- 다시 Ubuntu 터미널로 돌아 오면 `$ bundle exec jekyll serve` 를 실행하여 접속합니다.
- 이제 실시간으로 수정사항을 확인할 수 있습니다.

<br>

## 5. Conclusion

사실 코드만 알고 있으면 그렇게 어려운 작업은 아닙니다.  
설치하고 재부팅하고 설치하고 재부팅하고 .. 블로그 폴더로 이동하고 설치하고 재부팅하고 ..  
약간의 번거로움을 지나고 나면 실시간으로 확인할 수 있으니 노력을 들여볼 만 합니다.

완벽하지 않은 사람인 저로선 글을 작성하고 나면 늘 오타를 발견합니다.  
수정하고 글을 올렸는데 바로 확인할 수 없다면 끝내지 못한 과제를 바라보는 느낌이라 불편하더군요.  
그래서 저는 이렇게 실시간으로 확인할 수 있게 만드는 것이 중요했습니다.  
이제 조금은 속 시원하게 글을 작성하고 바로 확인하는 맛을 느껴봐야겠습니다.

질문이나 더 간단한 방법, 또는 추가로 덧붙이실 의견이 있으신 분들은 언제든 댓글을 남겨주세요~

<br>

> Mahalo~~
