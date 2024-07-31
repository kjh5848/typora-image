# git 기본 브랜치 설정하기

```
git config --global init.defaultBranch <브랜치 이름> #기본 브랜치로 변경
```

git 버전이 2.28이상이면 기본 브랜치가 main입니다. 하지만 그 이전에 다운을 받았다면 기본 브랜치가 master일 가능성이 높습니다. 위 명령어로 기본 브랜치를 원하는 브랜치명으로 변경할 수 있습니다.

`git config --global init.defaultBranch main`을 하면 main이 기본 브랜치로 설정이 됩니다.

> [!caution]
>
> `git config --global init.defaultBranch main`를 하고 새로 git init을 한 브랜치만 `main`으로 설정되어 보입니다. 기존 master 브랜치는 변경되지 않습니다.

<br>

# git 자격

의도치 않게 다른 사람의 컴퓨터로 git에 push할일이 생긴다면 아마 내 gtiHub에 원래 컴퓨터 주인의 gitBub계정으로 기록이 남겨질 것입니다. 그럴때는 자격증명관리자로 접근하여 기존 gitHub를 제거해줘야 합니다. 

<br>

#### 윈도우에서 GitHub 자격 증명 제거

1. 자격 증명 관리자(Credential Manager) 사용:
   - **시작 메뉴**에서 "Credential Manager" 또는 "자격 증명 관리자"를 검색하고 엽니다.
   - "Windows Credentials" 또는 "윈도우 자격 증명" 탭을 선택합니다.
   - 저장된 자격 증명 목록에서 `git:https://github.com` 또는 관련된 항목을 찾아 제거합니다.

#### 맥에서 GitHub 자격 증명 제거

1. 키체인 접근(Keychain Access) 사용:
   - **애플리케이션** > **유틸리티** > **키체인 접근(Keychain Access)**을 엽니다.
   - 왼쪽 상단의 검색창에 `github`를 입력하여 관련된 자격 증명을 찾습니다.
   - GitHub 관련 자격 증명을 선택하고, **Delete** 키를 눌러 제거합니다. 또는, 자격 증명을 마우스 오른쪽 버튼으로 클릭하고 "삭제(Delete)"를 선택합니다.

<br>
