# 빌드 / 배포

CMP 프로젝트 빌드, 배포 과정

github에 소스코드 올리면 jenkins로 자동 빌드될 때 Dockerfile을 이용해서 Docker image가 생성된다.

이 도커 이미지는 도커 이미지를 관리하는 사내 registry 서비스 \(ReDii\)에 올라간다. \(docker image push\)

\(ReDii에서 pre 0~4 중에 올라가있으니까 확인해보기\)

이렇게 만든 이미지는 argoCD에서 K8S로 배포된다.

\(out of sync라는 버튼이 보이면 sync 버튼 눌러주면 된다.\)

Dockerfile

Dockerfile로 도커 이미지를 빌드

nginx도 도커 이미지로 불러올 수 있는데 그리고 nginx의 config도 수정하고 싶은데

docker 이미지 안에 nginx.config에 우리가 쓰고 싶은 내용을 덮어 써서 원하는 설정으로 nginx를 띄우자.

```text
# nginx 불러오자
FROM sds.redii.net/cmp-base/nginx:1.19.6-cmp.2
```



Dockerfile 작성

Docker 로그인

* docker login ....

Docker 빌드

* docker build -t ${저장할 이미지 이름} .

Docker 실행

* docker run --rm -it -p 8080:8080 ${실행할 이미지}:latest

