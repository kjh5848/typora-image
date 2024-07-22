# 🔥지옥에서 온 관리자 Git🔥

> **여러 명의 개발자가 협력하여 프로젝트를 관리할 수 있도록 돕는 도구**

<br>

## 1️⃣3️⃣- 브랜치 포인터 이해하기

---

[TOC]

---

## 1) 브랜치 포인터

- #### 브랜치 포인터란?

![image-20240721224322435](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721224322435.png)

> 브랜치 포인터는 Git에서 브랜치의 현재 상태를 가리키는 참조(reference)입니다. 이는 특정 브랜치의 최신 커밋을 가리키며, 브랜치의 히스토리와 상태를 추적하는 데 사용됩니다.

<br>

## 2) fast-forward의 브랜치 포인터

- #### fast-forward의 브랜치 포인터는 병합을 할때 어떻게 움직일까요?

![image-20240721231046978](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721231046978.png)

> Fast-Forward Merge는 병합 과정에서 브랜치 포인터를 이동시키는 방식으로 작동합니다. 이는 두 브랜치 간에 다른 변경 사항이 없고, 병합 대상 브랜치가 현재 브랜치의 최신 커밋 이후에 추가된 커밋만을 포함할 때 가능합니다. 이 경우, 병합은 단순히 브랜치 포인터를 최신 커밋으로 이동시키는 방식으로 처리됩니다.

<br>

## 3) 3-way merge의 브랜치 포인터

- #### 3-way merge의 브랜치 포인터는 병합할때 어떻게 움직일까요?

![image-20240721232443209](https://raw.githubusercontent.com/kjh5848/typora-image/main/image/image-20240721232443209.png)

> 3-Way Merge에서는 Fast-Forward Merge와 달리 브랜치 포인터를 단순히 이동시키는 것이 아니라, 새로운 병합 커밋을 생성하여 두 브랜치를 병합합니다. 이 과정에서는 공통 조상(commit)을 기준으로 두 브랜치의 변경 사항을 비교하고, 이를 기반으로 새로운 병합 커밋을 만들어 브랜치를 병합합니다.