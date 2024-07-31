# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

# 9️⃣- Git 기본기 실습 세번째

> [!note]
>
>  📋**이번 강의 새로운 명령어**
>
> 1. clear

[TOC]

<hr>

## 1) 복습(ex02)

- #### ex02폴더를 만들고 8강에서 했었던 내용을 복습하면서 새로운 시나리오로 진행합니다.

![image-20240720172125066](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720172125066.png)

> ex02 폴더 생성

![image-20240720172323352](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720172323352.png)

> ex02에 git bash를 열어서 git init를 실행합니다.

![image-20240720172720665](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720172720665.png)

> test1.txt 텍스트 파일을 생성하여 '1.첫번째 내용' 을 적어 저장해줍니다.

![image-20240720174105752](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720174105752.png)

> 'git status'를 해보면 test1.txt파일이 빨간색으로 표시된걸 알 수 있고, 이는 git이 변경된 부분을 감지하고 있다는 걸 확인할 수 있습니다. 

![image-20240720174043775](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720174043775.png)

> 'git add .' 을 한 후 'git status'를 하면 변경된 파일이 초록색이 된걸 확인할 수 있고 이는 변경된 파일을 'git add .'로 인덱스 영역에 등록되었다는 걸 확인할 수 있다.

![image-20240720174030771](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720174030771.png)

> 'git commit -m"1. 첫번째 사진" '을  헤더영역(사진첩)에 보관을 한 다음  'git status'를 하게 되면 이제는 변경된 파일이 없으니 아무것도 나오지 않을것이다.  

---

  

## 2) 새로운 시나리오(test2.txt)

- #### test2.txt 파일을 만들고 새로운 시나리오를 적용해봅니다.

![image-20240720180758070](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720180758070.png)

> test2.txt 파일을 만들고 '1.첫번째 내용'이라고 저장합니다.

![image-20240720175341718](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720175341718.png)

> test2.txt 파일을 만들고 'git status'를 통해 변경감지된 파일을 확인해봅니다.

> [!note]
>
> ![image-20240720180542047](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720180542047.png)
>
> **clear -> 코드를 깔끔하게 정리 할 수 있습니다.**

![image-20240720181300203](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720181300203.png)

> **'git commit -m"2. 두번째 사진" '**을 하고 **'git log'**에서 보이는 첫 커밋과 두번째 커밋의 해시를 보여줍니다.

![image-20240720181458654](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720181458654.png)

![image-20240720181534741](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720181534741.png)

> 현재 해시가 두번째 커밋의 해시 값과 동일하다는 걸 알려줍니다. 또한 헤더영역에 헤더가 어떻게 해시는 가리키고 있는지 이를 그림을 통해 설명합니다.

### 그림1

![image-20240720182801278](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720182801278.png)

- #### 현재 헤더는 어디를 가리키고 있나요?

> 현재 헤더는 **master**라는 브랜치의 첫번째 커밋의 해시인 84a8(84a835f8e8e39b6b6d7329fe324a1444ec498b09)을 가리키고 있습니다.

### 그림2

![image-20240720191829692](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720191829692.png)

- ####  test2.txt를 만들고 두번째 커밋을 하고 난 후 헤더는 어디를 가리키고 있을까요?

> 현재 헤더는  master의두번째 커밋의 헤더인 da3f(d3f4a7c88a7cb7ae77546fe1b21961c9e9a3a444)를 가리키고 있습니다. 아까 .git폴더의 refs/heads/master 파일에서 확인했던 해시값이 왜 두번째와 동일한지 이해할 수 있습니다.

  



##   3) test1.txt 내용 추가

- #### test1.txt에 새로운 내용을 저장하여 확인해보겠습니다.

![image-20240720192448361](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720192448361.png)

![image-20240720192552150](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720192552150.png)

> test1.txt에 '2. 두번째 내용을' 저장을 한뒤 'git status'를 하면 new file이 아닌 modified(변경하다, 수정하다)라고 뜨는걸 확인할 수 있습니다. 그럼 test1.txt는 '1. 첫번째 내용'의 버전과 test1.txt '. 두번째 내용'의 버전 이렇게 두가지가 있구나 라는걸 알 수 있습니다.

- #### 다음 'git add .' 'git commit -m"3. 세번째 사진" '을 하면 어떻게 될까요?

### 그림1

![image-20240720195936949](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720195936949.png)

> 그림을 보면 두번째 해시를 세번째에서 참조를 하고 있는 모습과 헤더는 세번째는 가리키고 있는걸 예상할 수 있습니다. 그럼 직접 명령어를 쳐보면서 확인해보겠습니다.





> [!important]
>
> - **직접해보기**
>
> ![image-20240720200401119](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720200401119.png)
>
> **이제 'git add . '  -> ' git commit ' 을 한 뒤에 master파일의 해시와 git log를 통해 3. 세번째 내용의 커밋 해시를 비교 해보세요.**

![image-20240720200545423](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240720200545423.png)

> 확인하면 3번째 커밋의 해시와 master의 해시가 동일하다는 걸 확인할 수 있습니다.