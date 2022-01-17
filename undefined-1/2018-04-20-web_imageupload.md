---
layout: post
title: Web Development&#58; Image Upload
tags:
  - Web development
---

# Node.js 기반 웹 어플리케이션에서 이미지 업로드하기

이 프로젝트는 [https://github.com/kuongee/The-First-Web-Page](https://github.com/kuongee/The-First-Web-Page) 공개되어있습니다.

## 1. Motivation

웹 기반 어플리케이션에 대한 이해를 돕기 위해 웹 개발 스터디에 참여\
(kenu님의 도움을 받아 스터디 및 개발 진행)

그 중 이미지 업로드하는 부분에 대한 기록

Node.js / javascript, ajax / MariaDB\
개발환경: Visual studio code

## 2. 이미지 업로드

![첫 페이지 모습](../.gitbook/assets/web\_imageupload1.png)

### 1. multer 사용

* multer 사용법 [https://github.com/expressjs/multer](https://github.com/expressjs/multer)

### 2. Database

* MariaDB 사용

#### table 구성

```
테이블명: image
스키마: id, path
```

#### table 적용

image 테이블에는 이미지의 제목(path)만 저장하고 개별 아이디 번호를 부여

이미지의 제목은 앞부분에 타임스탬프를 덧붙여 저장 → multer에서 처리

### 3. 목록 보이기

#### 페이징 처리

(kenu님 webbs 참고함)

* 현재 페이지 번호를 넘겨주고 시작점을 설정해주고 원하는 갯수만큼을 offset을 설정하고\
  DB에서는 아이디 번호 역순으로 뽑아옴

#### 삭제하기

* 목록에서 원하는 이미지를 선택하여 삭제\
  DB와 로컬 디렉토리에서 모두 삭제

## 3. Reference

* kenu님 [https://github.com/kenu/okweb](https://github.com/kenu/okweb)
* kenu님 youtube 강좌(파일 업로드 그리고 DB)
