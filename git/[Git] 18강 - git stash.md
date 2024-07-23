# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣8️⃣- Git stash

> [!note]
>
> 📋**이번 강의 새로운 명령어**
>
> 1. git stash
> 2. git stash pop
> 3. git stash apply
> 4. git stash list

---

[TOC]

---

## 1) stash란?

- #### stash란 뭘까요?

![image-20240723104759640](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723104759640.png)

> - ##### stash는 물건을 치우다, 감추다라는 뜻입니다. 
>
> - ##### stash를 사용하는 이유
>
>   - 변경사항을 커밋하기엔 아직 이른 경우
>   - 다른 브랜치로 체크아웃할 때 변경사항을 유지하고 싶은 경우
>   - 변경사항을 일시적으로 저장하고 싶은 경우

<br>

## 2) stash 이해하기

- #### topic 브랜치에서 로그인 만드는 일을 하고 있었습니다. 그런데 상사가 main 브랜치에서 아이디 중복체크를 만들어라고 합니다. 이때는 어떻게 해야할까요?

그림

## 3) stash 실습하기

### 1. stash 미사용

- #### topic에서 stash를 사용하지 않고 main으로 이동하여 git status로 변경내용이 main 브랜치에 이동하는지 확인하기

  - ex09 폴더를 만들고 시작합니다.
  - touch 회원가입.txt
  - git add . -> git commit -m"회원가입"
  - git checkout -b topic
  - touch 로그인.txt

#### ![image-20240723173458264](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723173458264.png)

> 회원가입.txt 파일을 만들고 topic 브랜치를 생성하여 로그인.txt 파일을 만들어줍니다.  git status로 확인하면 워킹 디렉토리에 변경내역이 감지 되어있는걸 확인할 수 있습니다. 이제 main으로 checkout해서 다시 git status를 해보겠습니다.

<br>

![image-20240723173728187](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723173728187.png)

> checkout main브랜치로 이동해서 status를 확인해보면 분명 main에서는 회원가입을   커밋하고 나서 topic에서 로그인.txt 파일을 만들었고 다시 main으로 왔는데 status에는 현재 main 워킹 디렉토리에서 변경내역을 확인할 수 있습니다.

> [!important]
>
> Git은 브랜치를 전환할 때 워킹 디렉토리와 인덱스를 클린 상태로 만들고자 합니다. 하지만, 작업 중인 변경 사항(수정되었으나 커밋되지 않은 파일)은 워킹 디렉토리와 인덱스에 남아 있습니다. 따라서, 브랜치를 전환할 때 이러한 변경 사항이 자동으로 새로운 브랜치로 이동하게 됩니다.

<br>

- #### 그럼 main에서 로그인을 커밋하면 어떻게 될까요?

![image-20240723174025987](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723174025987.png)

> 보시다시피 커밋을 남기고 topic으로 이동을 하니 로그인.txt파일도 사라지면서 main에 커밋이 되었고 브랜치 포인터도 topic은 회원가입만 가리키고 있는걸 확인할 수 있습니다.

<br>

### 2. stash 사용

- #### 로그인을 topic에서 stash를 사용해서 적용하는 방법을 배워보겠습니다.

  - 방금 만들었던 ex09 폴더의 파일들을 전부 지우고 시작합니다.(.git 포함)
  - touch 회원가입.txt
  - git add . -> git commit -m"회원가입"
  - git checkout -b topic
  - touch 로그인.txt

![image-20240723175048281](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723175048281.png)

> 위에서 했던 상황고 동일하게 만들어줍니다. 이번에는 git stash를 사용해서 topic 워킹 디렉토리에 있는 로그인.txt를 스테싱 영역에 넣어서 