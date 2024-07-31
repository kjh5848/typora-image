# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 8️⃣- Git 기본기 실습 두번째

> [!note]
>
>  📋**이번 강의 새로운 명령어**
>
> 1. git init
> 2. git status
> 3. git add .
> 4. git commit -m" "
> 5. git log

<hr>

[TOC]

<hr>

## 1) 작업영역(git init)


> 회원가입시 만들었던 gitworkspace/ex01 파일에서 git bash로 git init를 통해 폴더에 작업영역 선언하는 것을 보여줍니다.

![image-20240719175052857](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175052857.png)

![image-20240719175309656](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175309656.png)

> 윈도우 10이상은 shift + 마우스 우클릭 하면 바로 git bash를 확인할 수 있다.

![image-20240719175423281](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175423281.png)

> git init

![image-20240719175501586](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175501586.png)

![image-20240719175805383](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175805383.png)

![image-20240719175837371](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719175837371.png)

> 숨긴항목을 누르면 .git 파일이 된걸 확인할 수 있다. 이는 위 그림들처럼 ex01 파일에 작업영역이 선언되었다는 말과 같다.

![image-20240719180108107](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719180108107.png)

> ex01폴더안에 test1.txt 파일을 생성한 후 "1. 첫번째 내용"을 적어준뒤 저장합니다. 그럼 이제 파일을 확인해보겠습니다.

![image-20240719180443395](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719180443395.png)

> git status(상태확인) 위 빨간 박스를 번역 =>  커밋에 추가되는 것은 아무것도 없고 추적되지 않은 파일만 있음("git add"를 사용하여 추적) 즉, git add 를 통해 변경감지된 파일이 있으니 이걸 영구히 저장(git commit)을 하고 싶으면 git add를 해서 추적할 수 있게 해달라는 뜻입니다.

<hr>

<br>

## 2) 인덱스 영역(git add .)

![image-20240719180908162](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719180908162.png)

> git add .  => 전체 파일 등록  예) 10개, 100개, 1000개~~ 가능
> git add test1.txt => test1.txt 파일 1개만 등록
>
> (강추) gti add . 

![image-20240719181122627](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719181122627.png)

> git status를 다시 해보면 빨간색에서 초록색으로 바뀐걸 확인할 수 있다.

```
'git status'는 현재 .git으로 선언 되어있는 폴더의 변경된 파일의 상태를 확인할 수 있는 명령어이다.
```



![image-20240719181536385](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719181536385.png)

![image-20240719181628756](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719181628756.png)

> 해당 파일을 자세히 확인하고 싶으면 .git 파일에 들어가서 objects 파일로 가게되면 3가지 파일중 e6파일에 들어가 보면 된다. (e6 파일이 아닐수도 있다.)

![image-20240719181808403](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719181808403.png)



> 해시값을 확인할 수 있다. 그럼 이제 저장한 test1.txt파일을 헤더영역에 영구히 저장해보자.

<hr>

<br>

## 3) 헤더 영역(git commit -m"  ")

![image-20240719182920437](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719182920437.png)

![image-20240719183623416](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719183623416.png)

- 최초 설정 알려주기

> 처음 Git을 사용하게 되면 자신의 이름과 이메일을 설정해야 합니다.
>
> ```console
> git config --global user.name "Your Name"
> git config --global user.email "your_email@example.com"
> ```

![image-20240719183527432](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719183527432.png)

> git commit을 통해 헤더에 영구히 보관을 합니다.

![image-20240719184152784](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719184152784.png)

> 현재 상태는 위 그림과 같이 되어있습니다.

![image-20240719184413103](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719184413103.png)

- git log에 대해서 알려주기

> git commit으로 저장된 첫번째 사진의 내용을 확인할 수 있다.

- 마무리

```
작업영역, 인덱스영역, 헤더영역에 대해서 직접 명령어를 통해 적용하는 방법을 배워보았으며, 다음은 test2.txt를 만드는 새로운 시나리오를 만들어보면서 복습을 해보겠습니다.
```

