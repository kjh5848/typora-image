# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣5️⃣- three way merge 실습

> [!note]
>
> 📋**이번 강의 새로운 명령어**
>
> 1. git checkout -b <브랜치 이름>
> 1. vi 에디터 ->  ESC  -> :wq(저장하고 종료)

---

[TOC]

---

## 1) git checkout -b <브랜치 이름>

- 준비물 

  - ex06 폴더 생성

  - 'touch 회원가입.txt' 명령어로 파일 생성

  - git add . -> git commit -m"회원가입"

  - 'touch 로그인.txt' 명령어로 파일 생성

  - git add . -> git commit -m"로그인"

  - git checkout -b topic

  - 'touch 아이디중복체크.txt' 명령어로 파일 생성

  - git add . -> git commit -m"아이디중복체크"

> [!tip]
>
> ![image-20240722213230236](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722213230236.png)
>
> #### git checkout -b <브랜치 이름>
>
> - git branch <브랜치 이름> , git checkout <브랜치 이름> 이 두가지 명령어를 합친 명령어이다.

![image-20240722213421449](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722213421449.png)

> 위 로그처럼 준비를 해주면 됩니다.

<br>

## 2) 3-way merge 실습하기 1

- #### main에서 글쓰기를 만들고 merge를 하면 어떻게 될까요?

![image-20240722214124369](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722214124369.png)

> 우선 현재 HEAD가 어느 브랜치에 있는지 알아야 하는데요. 총 3가지가 있습니다.
>
> 1. git branch에서 *표시 브랜치
> 2. git log에서 HEAD
> 3. 명령줄에서 브랜치

<br>

#### main 브랜치 

![image-20240722215442650](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722215442650.png)

#### topic 브랜치 

![image-20240722215234098](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722215234098.png)

> 두 브랜치를 비교해 보면 각각 다른 글쓰기와 아이디중복체크라는 다른 파일들을 가지고 있습니다. 여기서 우리는 두 브랜치가 다른 형상을 가지고 있다는걸 알 수 있습니다.

<br>

![image-20240722220010971](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722220010971.png)

> 위 그림처럼 HEAD가 있는 main브랜치에서 topic을 merge하면 두 브랜치는 각각 다른 변경사항을 가지고 있어 공통조상을 찾게 되고 이후 3-way merge가 일어나게 됩니다.

<br>

## 3)  3-way merge 실습하기 2

- #### 3-way merge가 일어나면 커밋 로그는 어떻게 남겨지게 될까요?

![image-20240722220444015](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722220444015.png)

![image-20240722220400482](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722220400482.png)

> git bash에서 merge topic을 하게 되면 vi 에디터가 나옵니다. (vi 에디터는 나중에 rebase라는 걸 배울때 더 자세히 배우도록 하겠습니다.) 여기서는 ESC 를 누르고 :wq(저장하고 종료)를 입력하고 엔터를 눌러줍니다.

![image-20240722220715067](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722220715067.png)

> 그리고 메세지에 fast-forward라는 메세지가 없고 3-way merge가 되었다는 걸 확인할 수 있습니다.

![image-20240722220931082](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722220931082.png)

> log를 해보면 현재 main에서 merge가 된 topic의 커밋 로그중 '아이디 중복체크' 를 확인할 수 있습니다. 또한 HEAD가 있는 커밋은 Merge branch 'topic' 이라고 해서 3-way merge를 하게 되면 강제로 커밋 로그를 만들어서 기록을 남긴다는 것도 확인할 수 있습니다.