# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣2️⃣- Git branch 기본개념

---

[TOC]

---

## 1) Git Branch란?

- #### git 브랜치란 무엇일까요?

![img](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/types-of-git-branch-main.png)

> Git 브랜치는 본질적으로 독립적인 개발 라인입니다. 새 기능이나 버그 수정 작업을 할 때 브랜치를 사용하여 다른 팀 구성원의 작업과 분리할 수 있습니다.

![image-20240721204137216](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721204137216.png)

> 이때까지 우리는 헤더영역을 브랜치라고 하였는데요. git을 처음 만들게 되면 무조건 **main** 브랜치가 만들어지게 되어있습니다. 

<br>

## 2) Branch 개념

- #### **[블로그 만들기 프로젝트]**  시나리오를 통해 브랜치가 어떤 역할을 하는지 알아보겠습니다.

![image-20240721204809947](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721204809947.png)

> [!tip]
>
> 간단한 이해를 돕기 위해 **[블로그 만들기 프로젝트]** 시나리오를 통해 설명해 드리겠습니다.
>
> - 첫번째 계획
>   1. main 브랜치에 회원가입 -> 로그인 -> 글쓰기 기능을 만듭니다.
>   2. 하지만 A라는 직원은 로그인을 할때 중복체크라는 걸 새롭게 만들고 싶다고 합니다.
>   3. 상사는 기존 계획과는 다른기 때문에 따로 작업하라고 합니다.
>   4. 그렇게 A라는 직원은 새로운 idea브랜치를 만들어서 중복체크라는 기능을 만들게 됩니다.

> 위 그림처럼 브랜치는 각각의 기능을 추가로 만들고 또는 각 기능의 버그를 수정하거나 업그레이드할때 그 기능의 브랜치를 만들어서 독립적으로 개발 라인을 만들어 작업할 수 있습니다.

<br>

## 3) Branch(3 - way merge)

- #### A직원이 중복체크를 3단계에 걸쳐서 완성을 하였습니다. 그리고 상사는 중복체크 기능이 마음에 들어서 기존 main 브랜치에 합치고 싶어합니다. 어떻게 하면 될까요?

![image-20240721210531513](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721210531513.png)

> A직원이 1~3단계에 걸쳐서 중복체크를 완료하였습니다.  상사는 idea 브랜치에서 확인을 해보니 중복체크가 너무 잘되서 마음에 들었습니다. 결국 main 브랜치에 idea 브랜치를 합쳐서 사용을 하고 싶어하는데요. 
>
> 이때 **3 - way merge**를 하게 됩니다.

> [!important]
>
> #### 3 - way merge는 형상이 다를때 적용된다.
>
> ![image-20240721211907476](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721211907476.png)
>
> 먼저 형상을 보게 되면 main과 idea 브랜치 둘다 회원가입과 로그인은 같은 해시를 참조하고 있기 때문에 두 브랜치의 공통된 해시라고 볼 수 있습니다. 따라서 **공통조상**이라고 할 수 있는데요. 그 아래 글쓰기와 1~3단계 중복체크는 형상이 다른데요. 이때  git은  **3-way merge**를 하게 됩니다. 

 <br>

![image-20240721211931904](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721211931904.png)

- #### 3-way merge란?

> **3-way merge**는 Git에서 두 개의 브랜치를 merge(병합)할 때, 공통 조상 커밋을 이용하여 병합하는 방법입니다. 병합하려고 하는 두 커밋의 공통조상을 찾고 변경사항을 비교하여 통합하게 됩니다. 

<br>

## 4) Branch(fast-forward  merge)

- #### 새로운 시나리오를 통해 fast-fowrad merge를 알아봅니다.

![image-20240721214712377](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721214712377.png)

> 앞선 main과는 다른 커밋 로그를 가지고 있습니다. 형상을 보면 둘다 공통조상을 가지고 있고 변경사항을 보니 따로 변경된 내용이 없고 idea 브랜치만 커밋을 가지고 있어 3-way merge가 일어날 필요가 없이 바로 merge(병합)가 일어나게 됩니다.
>
> 이를, **fast-foward merge**라고 합니다.

