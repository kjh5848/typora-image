# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣6️⃣- merge 충돌해결

---

[TOC]

---

## 1) merge 충돌 이해하기

- #### 3-way merge를 하게 되었을때 같은 파일이 다른 내용을 가지고 있다면 어떻게 될까요?

![image-20240722225029821](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722225029821.png)

> 1. main에서 로그인 파일을 생성
> 2. 로그인 파일의 내용을 **'로그인 라디오 버튼'**으로수정합니다. 
> 3. topic 브랜치를 만들고 이동합니다.
> 4. topic의 로그인 파일의 내용을 **'로그인 체크박스'**로 수정합니다.

<br>

![image-20240722225423701](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722225423701.png)

>  로그인 라디오 버튼과 로그인 체크박스가 3-way merge를 할때 공통조상을 찾고 변경사항을 확인하게 됩니다. 그런데 같은 파일에 각각 다른 내용들이 있으면 git은 conflict(충돌)가 되어 어떤 파일을 선택해야하는지 알 수가 없습니다. 그래서 git은 우리 개발자에게 선택 할 수 있게 해줍니다.

![image-20240722225449530](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722225449530.png)

> conflict(충돌)이 나면 git은 개발자가 어떤 브랜치의 내용을 병합할건지 표시를 해줍니다.

<br>

## 2) merge 충돌 준비하기

- #### 이제 직접 실습을 통해 merge 충돌을 해결해 보겠습니다.

  - ex07 폴더를 만들고 시작합니다.

![image-20240722230513984](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722230513984.png)

![image-20240722230922300](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722230922300.png)

> - 로그인 버튼으로 내용을 저장해줍니다.
>
> 1. touch 로그인.txt
> 2. 내용 : 로그인 버튼으로 저장
> 3. git add . -> git commit -m"로그인"

<br>

![image-20240722231419581](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722231419581.png)

![image-20240722231916411](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722231916411.png)

> - topic 브랜치에서 로그인 체크박스로 내용을 저장합니다.
>
> 1. git checout -b topic
> 2. 내용 : 로그인 체크박스로 저장
> 3. git add . -> git commit -m"로그인 체크박스"

<br>

![image-20240722232031491](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722232031491.png)

![image-20240722232224268](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722232224268.png)

> - main에서 로그인 라디오 버튼으로 내용을 저장합니다.
>
> 1. git checkout main
> 2. 내용 : 로그인 라디어 버튼으로 저장
> 3. git add . -> git commit -m"로그인 라디오 버튼"

<br>

## 3) merge 충돌 해결하기!

![image-20240722232729747](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722232729747.png)

- 로그를 읽어야 디버깅을 할 수 있습니다.

- CONFLICT (content): Merge conflict in 로그인.txt
  Automatic merge failed; fix conflicts and then commit the result.

> 번역 -> 충돌(내용): 로그인.txt에서 충돌 병합
> 자동 병합이 실패했습니다. 충돌을 수정한 다음 결과를 커밋합니다.

<br>

![image-20240722232857483](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722232857483.png)

> [!CAUTION]
>
> 로그인.txt 파일을 열어보면 이렇게 HEAD에 있는 내용과 topic에 있는 내용을 알려주고 선택할 수 있게 합니다.
>
> 
>
> - #### 로그인 라디오 버튼을 병합할때
>
> ![image-20240722233127442](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722233127442.png)
>
> - #### 로그인 체크박스를 병합할때
>
> ![image-20240722233219269](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722233219269.png)
>
> **<<<<<<<<<<<<< HEAD, ======, >>>>>>>>**  이 부분은 다 지워야 합니다.

<br>

![image-20240722233629615](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722233629615.png)

> 내용을 다 수정하였고 저장을 하고 나서 git을 확인하면 브랜치에 MERGING이라고 되어있는걸 확인할 수 있습니다. 그리고 status를 확인하면 현재 변경된 내용이 있다고 합니다. 
>
> 그럼 이제 커밋을 하여서 MERGING을 끝낼 수 있습니다.

<br>

![image-20240722233947337](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240722233947337.png)

> 이렇게 MERGING상태에서 빠져나온걸 확인할 수 있고 커밋 로그도 마지막 남긴 로그로 잘 되어있는걸 확인할 수 있습니다.