# \[Git]

#### 버전관리 시스템의 종류

* 로컬 버전 관리 시스템
* 중앙집중식 버전 관리 시스템 : 하나의 서버에서 모든 파일을 저장 / 클라이언트는 파일 (snapshot)들을 가져옴
* 분산버전 관리 시스템 : 클라이언트는 전체 저장소 (repository)를 가져옴\
  [https://git-scm.com/book/ko/v1/시작하기-버전-관리란%3F](https://git-scm.com/book/ko/v1/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-%EB%B2%84%EC%A0%84-%EA%B4%80%EB%A6%AC%EB%9E%80%3F)

#### Git

* 분산 버전 관리 시스템
* 파일의 변화를 저장하는 버전관리 시스템들이 있지만 Git은 시간 순으로 프로젝트의 스냅샷을 저장

![https://git-scm.com/book/ko/v1/Git의-기초-수정하고-저장소에-저장하기](<../../.gitbook/assets/image (12).png>)



* Commit
  * 파일 및 폴더의 추가/변경 사항을 저장소에 기록
* Work tree / Index
  * 저장소 <----- 인덱스(가상공간) <----- 작업트리(폴더)
  * 인덱스에 파일 상태를 기록: Staging
  * 저장소로 커밋

Reference\
\- [https://backlog.com/git-tutorial/kr/](https://backlog.com/git-tutorial/kr/)
