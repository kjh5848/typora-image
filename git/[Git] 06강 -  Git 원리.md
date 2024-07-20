# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 6️⃣- Git 원리(3가지 영역)

<hr>

- 실무에서는 어떻게 써요? 라는 질문이 많습니다.


```
Git의 원리를 이해하고 사용하고 난 후 Git에 대한 원리에 답변을 할 수 있어야 한다. 즉, Git을 사용해보고 Git의 원리는 어떻게 되고 협업에는 어떻게 활용할 수 있는지에 대한 내용을 답변할 수 있으면 된다.
```

<hr>

## 1) 작업영역

![image-20240718161539756](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240718161539756.png)

- 작업영역 선언, git init

```
A라는 폴더에 작업을 하겠다는 작업영역을 선언하며 폴더의 변경 내용을 감지한다.
```

<hr>

<br>

## 2) 인덱스 영역

![image-20240718163511629](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240718163511629.png)

- 변경된 내용을 저장하는 곳 인덱스 영역, git add 

```라고 
변경된 내용을 저장할때는 git add 라는 명령어를 사용합니다. git add는 변경된 내용을 Tree(목차)구조로 저장을 합니다. test1.txt 파일은 Blob (객체)라고 하며 파일 내용자체를 저장하는 객체입니다. 
```

> Blob (Binary Large Object

<hr>

<br>

### 3) 헤더 영역

![image-20240719151201306](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719151201306.png)

- 영구적으로 저장을 하는 곳 헤더 영역, git commit

```
인덱스에 있는 파일의 내용을 영구히 기록하기 위해서는 브랜치라는 헤더 영역에 저장을 해야하며 git commit 명령어를 사용하여 영구히 기록을 합니다. 
```

<hr>
<br>

## 4) test2.txt 생성시 

![image-20240719153220706](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719153220706.png)

- test1.txt를 만들고 나서 test2.txt를 만든다면 tree 구조는 어떻게 만들어질까요?

```
 test2.txt를 만들고 git add -> git commit을 한다면 해더 영역에는 처음 v1 밑에 v2의 가지가 하나더 생겨나고 v2는 처음 만들었던 test1.txt를 가지고 있습니다. 그림만 본다면 v2는 test1.txt,test2.txt 파일들을 가지고 있는 것처럼 보이지만 각 tree는 해시값으로 되어 있어 test1.txt 파일 그 자체를 가지고 있지는 않습니다. 따라서 파일의 내용을 가지고 있는게 아닌 파일 Blob의 해시값을 가지고 있습니다.
```

> 자바나 자바스크립트를 배우셨다면 변수를 정의하고 변수의 주소값만 가지고 있다고 이해하면 됩니다.

<hr>
<br> 

### 5) test2.txt의 내용을 추가 한다면?

![image-20240719154433793](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240719154433793.png)

- test2.txt의 내용을 변경하여 git commit을 한다면 어떻게 될까요? 그리고 이 구조의 장점은 무엇일까요?

```
인덱스 영역을 자세히 보면 각각의 파일의 tree를 변경이 된 tree에 해시값으로 포함이 되어 있는걸 확인할 수 있습니다. 여기서 만약 
```

- test2.txt(2)를 만들기 전으로 복구 하고 싶다고 하면 어떻게 될까요? 

```
모든 tree가 히스토리를 다 가지고 있기 떄문에 보라색으로 된 tree만 복사 한다면 바로 복구를 할 수 있습니다. 또한, 백업로그를 다 가지고 있어 내가 원하는 특정한 시점으로 복구를 할 수 있습니다.
```

- 마무리

```
이렇게 협업이 용이하고 백업과 복구에 좋은 Git DVCS에 대해서 배워 봤습니다. 다음 강의는 기본기의 실습을 해보도록 하겠습니다.
```







