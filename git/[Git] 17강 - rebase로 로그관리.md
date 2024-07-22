# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣7️⃣- rebase로 로그관리

> [!note]
>
> 📋**이번 강의 새로운 명령어**
>
> 1. git rebase -i HEAD~<원하는 커밋 개수>

---

[TOC]

---

## 1) rebase 란?

![Git Rebase: A Practical Guide](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/git-rebase-practical-guide.png)

특정 브랜치의 변경 사항을 다른 브랜치의 최신 상태 위에 다시 적용하는 작업을 의미합니다. 이를 통해 병합 히스토리를 깔끔하게 유지하고, 브랜치 간의 충돌을 최소화할 수 있습니다. Rebase는 주로 feature 브랜치를 main 브랜치에 병합하기 전에 사용되어, 마치 모든 작업이 연속적으로 일어난 것처럼 히스토리를 정리합니다.

- #### merge와의 다른점은 무엇일까요?

> **Merge**는 두 브랜치를 통합하여 병합 커밋을 생성하며 히스토리를 보존합니다.
>
> **Rebase**는 한 브랜치의 커밋을 다른 브랜치 위에 다시 적용하여 히스토리를 깔끔하게 만듭니다.

<br>

- #### rebase는 기본 리베이스(Basic Rebase)와 인터랙티브 리베이스(Interactive Rebase)가 있습니다.

> ##### 1. 기본 리베이스 (Basic Rebase)
>
> 기본 리베이스는 특정 브랜치의 커밋을 다른 브랜치 위에 재적용하는 가장 일반적인 형태의 리베이스입니다. 이를 통해 최신 커밋을 기반으로 작업을 계속할 수 있으며, 히스토리를 깔끔하게 유지할 수 있습니다.
>
> ##### 2. 인터랙티브 리베이스 (Interactive Rebase)
>
> 인터랙티브 리베이스는 기본 리베이스의 기능에 더해, 커밋 히스토리를 편집할 수 있는 기능을 제공합니다. 이를 통해 커밋 메시지를 수정하거나, 커밋을 합치거나, 삭제하는 등의 작업을 할 수 있습니다.

<br>

> [!tip]
>
> - #### rebase 인터랙티브 명령어
>
>   `pick`: 해당 커밋을 그대로 유지합니다.
>
>   `reword`: 커밋 메시지를 수정합니다.
>
>   `edit`: 커밋을 수정할 수 있게 합니다.
>
>   `squash`: 이전 커밋과 합칩니다.
>
>   `fixup`: 이전 커밋과 합치되, 커밋 메시지는 무시합니다.
>
>   `drop`: 커밋을 삭제합니다.

<br>

## 2) rebase squash 이해하기

- #### rebase 명령어인 squash에 대해서 알려드립니다.

![image-20240723002034391](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723002034391.png)

> squash는 이전 커밋과 합치는 명령어입니다. 위 커밋 로그들을 보면 로그인 퇴근, 로그인 이름, 로그인 완료를 하나의 커밋으로 만들어서 깔끔하게 만들고 싶을때 사용합니다.

<br>

- #### 왜 과거의 커밋으로만 합쳐야 할까요?

![image-20240723002749788](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723002749788.png)

> git rebase는 순차적으로 커밋을 합치기 때문에 중간 커밋을 합치고 나서 나머지를 pick하는 것은 불가능합니다. 하지만 환경설정을 pick하고 로그인퇴근과 아픔은  squash, 로그인 완료를 pick으로 하면 순차적으로 커밋을 합치기 때문에 올바른 방식이라고 할 수 있습니다.
>
> - 환결설정(pick)
> - 로그인퇴근(squash)
> - 로그인아픔(squash)
> - 로그인완료(pick)

<br>

- #### 그럼 중간 커밋들을 합칠 수 있을까요?

![image-20240723003222039](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723003222039.png)

>  로그인퇴근(pick), 로그인아픔(squash)를 하면 중간 두개의 커밋도 squash가 가능합니다.

<br>

## 3) rebase 실습하기

- #### 시나리오에 맞춰서 파일들을 준비합니다.

  - ex08 폴더를 만들고 시작합니다.
  - A직원이 **환경설정완료**로 커밋을 하고 로그인을 만들고 있습니다.
  - 그런데 갑자기 상사가 퇴근을 하라고 해서 **로그인퇴근**이라고 커밋을 남깁니다.
  - 그리고 **로그인아파서퇴근**을 하나더 남겼습니다.
  - 다음날 출근하여 **로그인완료**를 남겼습니다.

![image-20240723004734072](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723004734072.png)

> 그런데 중간에 **로그인퇴근**과 **로그인아파서퇴근** 상사나 제 3의 개발자가 봤을때 너무 쓸데없는 로그가 있다고 생각할 수 있습니다. 커밋 로그를 남기다 보면 다양한 로그를 남기게 되는데 그럴때 rebase squash를 사용해서 커밋을 깔끔하게 정리할 수 있습니다.

<br>

![image-20240723012106585](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723012106585.png)

![image-20240723005648981](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723005648981.png)

> [!tip]
>
> - **명령 모드(Normal mode)**: 기본 모드로, 텍스트를 탐색하거나 명령어를 입력할 수 있습니다. `vi`를 처음 열 때 이 모드로 시작합니다.
>
> - **입력 모드(Insert mode)**: 텍스트를 입력할 수 있는 모드로, 명령 모드에서 `i`, `a`, `o` 등의 키를 눌러 전환할 수 있습니다.
>
>   ![image-20240723010440846](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723010440846.png)
>
>   i, insert키를 누르면 맨아래 -- INSERT --라고 되어있는 걸 확인할 수 있습니다. 그럼 이제 vi에디터에서 입력할 수 있습니다.
>
> - **명령 라인 모드(Command-line mode)**: 파일 저장, 종료 등 명령어를 입력할 수 있는 모드로, 명령 모드에서 `:` 키를 눌러 전환할 수 있습니다.

<br>

### 1 - rebase d(drop)

- #### 아래 Command 중 d로  커밋을 삭제해 보겠습니다.

![image-20240723010615223](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723010615223.png)

> i나 insert를 눌러 입력모드로 전환을 해줍니다.

![image-20240723010812462](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723010812462.png)

> d, drop 커밋 삭제를 해봅니다. 로그인아파서퇴근 해시 앞에 **'d'**를 적어줍니다.

![image-20240723011021910](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723011021910.png)

> esc누르고 맨 아래 '**:wq**'를 적어주고 엔터를 누릅니다.

![image-20240723011115649](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723011115649.png)

> 그럼 성공이 완료 되었고, log도 성공적으로 지워졌습니다.

>[!tip]
>
>- #### 복구하기(reflog)
>
>  - 혼자서 시도해보기~!
>
>![image-20240723011324180](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723011324180.png)
>
>git reset --hard 5957로 reset을 하면 된다.
>
>![image-20240723011422266](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723011422266.png)
>
>log를 보면 다시 잘 돌아간걸 확인할 수 있다.

<br>

### 2 - rebase r(reword)

- #### reword로 커밋을 이름을 수정할 수 있습니다.

![image-20240723012146600](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723012146600.png)

> 입력모드(i)로 전환하고 로그인아파서퇴근 해시 앞에 r(reword)를 놓고 -> esc ->  :wq로 저장합니다.

![image-20240723012511303](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723012511303.png)

> 그럼 제일 상단에 변경할 커밋 메세지가 노란색으로 되어있습니다. 입력모드(i)로 전환하고  위 커밋 메세지를 **'로그인꾀병부려서퇴근'**으로 변경 -> esc ->  :wq로 저장합니다.

![image-20240723012649592](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723012649592.png)

> 로그를 확인하면 변경되어있는걸 확인할 수 있습니다. 

<br>

### 3 - rebase s(squash)

- #### squash로 커밋로그를 합치는 걸 해보겠습니다.

![image-20240723012918401](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723012918401.png)

> 이제 3개의 커밋을 squash를 해보겠습니다.

![image-20240723013120362](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723013120362.png)

> 상단에 합치는 커밋을 s로 지정합니다. 그리고 esc -> :wq로 저장

![image-20240723013759731](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723013759731.png)

> 이렇게 에디터가 나오고 로그인퇴근, 로그인꾀병부려서퇴근을 로그인으로 합치면 됩니다.

![image-20240723013921338](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723013921338.png)

> 로그인으로 변경하고 :wq로 저장!

![image-20240723014009968](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240723014009968.png)

> 이후 로그를 확인해보면 하나의 커밋로그로 깔끔하게 정리된걸 확인할 수 있습니다.