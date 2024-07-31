# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣4️⃣- fast forward 실습

> [!note]
>
> 📋**이번 강의 새로운 명령어**
>
> 1. touch <파일이름.확장자>
> 2. git branch
> 3. git branch <브랜치 이름>
> 4. git checkout <브랜치 이름>
> 5. git merge <브랜치 이름>

---

[TOC]

---

## 1) 브랜치를 생성하고 기

- #### 간단한 시나리오를 통해 fast-forward 실습을 해보겠습니다.

  - ex05 폴더를 만들고 시작합니다.

> [!tip] 
>
> ![image-20240722200723757](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722200723757.png)
>
> #### touch <파일이름.확장자>  
>
> -  파일을 생성할 수 있다.

<br>

![image-20240722201127459](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722201127459.png)

> 1. 'touch 회원가입.txt' 명령어로 파일 생성
> 2. git add . -> git commit -m"회원가입"
> 3. 'touch 로그인.txt' 명령어로 파일 생성
> 4. git add . -> git commit -m"로그인

<br>

- #### 여기서 추가로 브랜치를 새롭게 만들어서 아이디 중복체크를 만들려면 어떻게 해야할까요?

> [!tip]
>
> ![image-20240722201915715](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722201915715.png)
>
> #### git branch
>
> - 로컬에 있는 브랜치들을 볼 수 있다.
>
> ![image-20240722202116177](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722202116177.png)
>
> #### git branch <브랜치 이름>
>
> - 새로운 브랜치를 생성할 수 있다.

<br>

![image-20240722202252079](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722202252079.png)

> git branch로 확인하면 main과 topic 두가지의 브랜치를 확인할 수 있는데요. 브랜치 포인터로 두개가 생겼습니다.
>
> 그리고 log를 확인해보면 **'로그인'** 커밋의 해시를 main과 topic의 브랜치 포인터가 가리키고 있습니다. HEAD는 이번 강의  마지막에 자세히 설명해드리겠습니다.
>
> 이제 topic 브랜치로 이동해서 진행해보겠습니다.

> [!tip]
>
> ![image-20240722202532886](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722202532886.png)
>
> #### git checkout <브랜치 이름>
>
> - 원하는 브랜치로 이동할 수 있다.

![image-20240722203418969](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722203418969.png)

> git checkout topic을 하고 난 후 touch 아이디중복체크.txt 파일을 생성해주고 add와 commit 을 해줍니다. 

<br>

- #### 그럼 이제 git log를 했을때 main과 topic의 브랜치 포인터는 각각 어디를 가리키고 있을까요?

![image-20240722203624064](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722203624064.png)

> topic은 아이디중복체크, main은 로그인을 가리키고 있습니다. 현재 브랜치는 topic에 위치해 있습니다.

<br>

- #### 브랜치를 main으로 옮기게 되면 어떤 커밋들이 남아있을까요

![image-20240722204233533](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722204233533.png)

![image-20240722203941380](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722203941380.png)

> ex05 폴더를 보면 위 topic 브랜치는 회원가입, 로그인, 아이디중복체크가 있고, 밑에 main브랜치에는 회원가입, 로그인 파일만 있는걸 확인할 수 있습니다. 이렇게 두개의 브랜치의 형상이 다르다는 걸 확인할 수 있습니다. 

<br>

## 2) 헤더알아가기

- #### git checkout을 배웠으니 HEAD에 대해서 알고 넘어가도록 하겠습니다.

![image-20240722210608765](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722210608765.png)

> 처음 main 브랜치에서 회원가입, 로그인을 만들고 topic 브랜치를 만들고 나서도 HEAD와 두 브랜치 포인터는  로그인 커밋을 가리키고 있습니다.

![image-20240722210549665](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722210549665.png)

> 이후 checkout topic을 하고 아이디중복체크.txt 파일을 만들고 나서 커밋을 남기면 HEAD는 topic에 만들어 집니다.

- 그리고 다시 git checkout main을 하면 HEAD는 어떻게 될까요?

![image-20240722210903275](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722210903275.png)

> HEAD만 main 브랜치로 옮겨질 겁니다. 그리고 파일은 회원가입과 로그인만 보일겁니다. 즉, HEAD는 자신이 작업하고 있는 브랜치를 가리킨다고 생각하면 됩니다.

<br>

## 3) merge하기

- #### topic을 main에 merge하면 어떻게 될까요?

![image-20240722211612709](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722211612709.png)

> merge를 하면 main과 topic브랜치의 포인터는 아이디중복체크를 기리키고, HEAD는 main브랜치를 가리키고 있습니다. 그리고 checkout을 main이나 topic으로 하더라도 두 브랜치 다 회원가입, 로그인, 아이디 중복체크를 가지고 있을겁니다. 이게 바로 fast-forward merge 입니다.
>
> 그럼 merge를 직접 해보겠습니다.

![image-20240722221426253](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722221426253.png)

> 이렇게 checkout main -> **'git merge topic'**을 하게되면 메세지에서 **fast-forward**를 확인할 수 있고, 아까전  ex05 폴더에서 main브랜치에서만 회원가입, 로그인을 확인할 수 있었지만 현재 ex05 폴더에서 아이디중복체크.txt 파일을 확인할 수 있습니다.

![image-20240722212236902](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722212236902.png)

> log도 확인을 해보면 아이디 중복체크를 두개의 브랜치 포인터가 기리키고 있는 걸 확인할 수 있습니다.

