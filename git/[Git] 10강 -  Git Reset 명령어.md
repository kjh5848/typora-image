# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 🔟- Git Reset 명령어

> [!note]
>
>  📋**이번 강의 새로운 명령어**
>
> 1. git reset --soft <해시 4자리>
> 2. git reset --mixed <해시 4자리>
> 3. git reset --hard <해시 4자리>

---

[TOC]

---

## 🤓복습

> [!important]
>
> - **목표!** - git log를 했을때 아래의 사진처럼 나오게 만들기!
>
> ![image-20240720214130517](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720214130517.png)
>
> 1. ex03 폴더 생성
>
> 2. **text1.txt** 파일 생성 
>
>    - **'1. 첫번째 내용'**을 적고 저장하기
>
>    - **git commit -m"1. 첫번째 사진"** 으로 커밋하기	
>
> 3. **test2.txt** 파일을 만들고 **'1. 첫번째 내용'**을 적고 저장하기
>
>    - **git commit -m"2. 두 두번째 사진"** 으로 커밋하기(오타 아님)

---

  <br>

## 1)되돌리기(git reset)

![image-20240720214130517](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720214130517.png)

- 위 복습을 통해 만들어진 로그를 확인 후 '2. 두두번째 사진' 처럼 커밋 로그를 잘못 남겼을때 어떻게 수정할 수 있을까요?

> [!note]
>
> #### reset의 종류
>
> 1. hard - 이전 변경내용( 파일)으로 돌아가고 싶을때
> 2. Mixed - 작업영역의 내용을 변경하고 싶을때
> 3. soft - 커밋 로그를 변경하고 싶을때



### hard

![image-20240720220934497](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720220934497.png)

> hard는 위 그림처럼 test2.txt를 완전히 지우는 명령어입니다. 헤더영역, 인덱스영역, 작업영역까지 모든걸 reset하여 test1.txt로 돌아가는 명령어입니다.

### mixed

![image-20240720220854440](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720220854440.png)

> Mixed는 헤더를 지정한 커밋으로 이동시키고, 인덱스영역을 현재 커밋 상태로 재설정하지만, 작업 디렉토리(작업 공간)에 있는 파일들은 그대로 유지합니다. 

### soft

![image-20240720220819392](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720220819392.png)

> soft는 헤더의 커밋 로그만 변경을 하고 싶을때 사용을 합니다. 결국 내가 원하는 특정 헤더로 이동한다고 생각하면 됩니다.

> [!important]
>
> ##### **그럼 지금 '2. 두두번째 사진'으로 되어있는 커밋로그는 어떤 reset을 사용하여 변경을 해야 할까요? **

<br>

## 2) gti reset --soft

- #### git soft를 사용하여 헤더의 위치를 이동하여 로그를 변경합니다.

![image-20240720222106567](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720222106567.png)

> **'git reset --soft <해시 4자리>'** 를 입력하여 특정 커밋으로 이동할 수 있습니다.

![image-20240720222238876](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720222238876.png)



> soft를 한 후 status와 log를 확인하면 현재 '**git add .**' 까지 되어있는 걸 확인할 수 있고, **'1.첫번째 사진'**의 로그만 나와있는걸 확인할 수 있다.



![image-20240720222424463](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720222424463.png)

> **'git commit -m"2. 두번째 사진" '**으로 다시 커밋을 한 후 log를 확인하면 수정된 로그를 확인할 수 있습니다.

<br>

## 3) git reset --mixed

![image-20240720222944614](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720222944614.png)

- #### test2.txt 파일의 내용을 **'1.첫번째 내용 - 안녕'** 처럼 변경을 하고 커밋을 남기고 싶습니다. 그럼 어떻게 할 수 있을까요?

![image-20240720223036397](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720223036397.png)

> **'git reset --mixed <해시 4자리>'**를 입력하고 status를 확인해보면 현재 test2.txt가 빨간색으로 되어있는 걸 확인할 수 있습니다. 이는 **'git add .'**로 인덱스 영역에 등록했던  tree 즉, Blob이 없어졌다고 이해할 수 있습니다.
>
> 그렇다면 이제 test2.txt파일에서 내용을 수정하고 다시 등록을 할 수 있습니다.

![image-20240720222944614](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720222944614.png)

![image-20240720223442249](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720223442249.png)

> test2.txt 파일에 **'1.첫번째 내용 -안녕'**으로 저장한 다음 'git add .' > 'git commit -m"2. 두번째 사진" ' 을 해줍니다. 그리고 log를 확인해보면 새롭게 등록된 커밋 로그를 확인할 수 있습니다.

<br>

## 4) git reset --hard

- #### 현재 특정 커밋에 대한 모든 내용 즉, 작업영역과 인덱스, 헤더를 모두 날리고 다른 파일을 만들고 싶다면 어떻게 해야 할까요?

![image-20240720224639756](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720224639756.png)

> **'git reset --hard <해시 4자리>'** 명령어를 실행하면 ex03 폴더의 test2.txt 파일이 사라진걸 확인할 수 있습니다.

> [!Caution]
>
> **hard는 사용시 많은 주의가 필요한 reset 명령어입니다. 특정 커밋의 모든 내용을 날려버리기 때문에 복구하기가 까다롭습니다.**

<br>

![image-20240720225057217](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720225057217.png)

> test2.txt가 없어진걸 확인이 되었다면 test3.txt파일을 만들어 줍니다.

![image-20240720225225689](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720225225689.png)

> add -> commit을 하여 저장을 해주게 됩니다.

---

> [!tip]
>
> 위 3가지 reset 중 가장 즐겨쓰는 명령어는 hard 입니다. 반변 soft, mixed는 거의 사용을 하지 않습니다. 물론 커밋 로그를 변경한다고 하면 soft 정도는 쓸 수 있겠지만 mixed는 거의 사용하지 않습니다. 
>
> 만약, 위 mixed 예제 처럼  test3.txt 파일에 **'1.첫번재 내용 - 안녕'**으로 내용을 수정하고 싶다고 하면 이렇게 하는게 나을 수도 있습니다.
>
> ![image-20240720225855472](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720225855472.png)
>
> ![image-20240720230009207](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720230009207.png)
>
> 이렇게 버전 커밋 로그에 버전 v2를 만들어서 변경 이력을 확인할 수 있게 하는 방법도 있습니다.
> "그럼 커밋 로그가 깔끔하지 않잖아요~" 라고 할 수도 있습니다. 하지만 나중에 커밋 로그를 깔끔하게 하는 방법도 있으니 배워보시고 편하신 방법을 사용하시면 됩니다.

---

<br>

## 5) 숙제

> [!important]
>
> **'2.두번째 사진'**으로 저장하였던 커밋으로 되돌리고 싶으면 어떻게 해야할까요? 

#### 

