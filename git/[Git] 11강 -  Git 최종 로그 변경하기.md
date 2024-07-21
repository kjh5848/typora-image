# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣1️⃣- Git 최종 로그 변경하기

> [!note]
>
> 📋**이번 강의 새로운 명령어**
>
> 1. git commit --amend -m"[커밋내용]"

---

[TOC]

---

## 1) 최초 커밋 로그 변경하기

- #### 최초 커밋에 오타가 나거나 내용을 잘못입력했을때 어떻게 변경할 수 있을까요?

  > [!tip]
  >
  > 이전 강의에서 배웠던 resert은 최초 커밋이 아닌 두번째 커밋에서 reset -- soft를 사용하여 커밋로그를 수정하였습니다. 특정 커밋으로 이동하고 변경하는게 아닌 최초 커밋인 첫번째 커밋에서 바로 변경하는 방법을 배워봅니다.

- **준비물**

  1. ex04 폴더를 생성합니다.
  2. test1.txt 생성
  3. git commit -m"test3.txt 생성 완료" 를 남깁니다.

![image-20240721173845659](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721173845659.png)

> 위 커밋처럼 **'git commit -m"test3.txt 생성완료" '**를 남겼습니다. 그런데 파일 이름은 test1.txt입니다. 이것을 amend 명령어를 사용하여 변경합니다.

![image-20240721173959083](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721173959083.png)

> **'git commit --amend -m"test1.txt 생성 완료" '** 를 해주고 log를 확인하면 변경된걸 확인할 수 있습니다.



## 2) amend의 장단점

- amend와 soft 그리고 hard의 차이는 무엇일까요?

![image-20240721184529905](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721184529905.png)

> amend를 알아보면서 soft와 hard의 차이점을 확인해보도록 하겠습니다.
>
> **장점** 
>
> - 첫번째 커밋 로그도 변경이 가능하다.
>
> **단점**
>
> - 현재 head로 지정된 커밋 로그만 변경이 가능하다.
>
> 즉, amend는 특정 커밋 로그를 변경하는게 불가능합니다. 그럴땐 reset의 soft를 사용하여 헤드를 이동시킨 후에 다시 커밋 로그를 적어주면 되고, 특정 커밋과 관련된 내용을 다 지우고 다시 커밋을 해도 된다면 hard를 사용해서 커밋 로그를 다시 남길 수도 있습니다.