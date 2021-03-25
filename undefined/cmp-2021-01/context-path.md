# 배포 시 context path 추가

context path

http://localhost:8080/ 으로 접속하던 것에 /console/을 붙여서 접속하게 하려고 한다. → http://localhost:8080/console

이 프로젝트에서는 nginx를 사용하고 있고 아래처럼 nginx는 nginx.conf 설정에 따라 서버가 실행된다.

예를 들면 아래 **location /** \(http://localhost:8080/\)로 들어오면 /html/ 하위에서 resource들을 찾으라는 의미이다.

그래서 실제로 nginx 루트 디렉토리에 위치한 html 디렉토리에 모든 프론트엔드 결과물을 넣어두면 html 디렉토리에서 자원들을 찾는다.

```text
# nginx.conf
.......
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   html;
            add_header 'Access-Control-Allow-Origin' '*';
            index  index.html index.htm;
        }

        location /bss { # 이렇게 프록시도 설정할 수 있다.
          proxy_pass   http://172.21.133.110:17000;
        } 

.......
}

.......
```

그런데 우리는 /console을 기준으로 분리해내고 싶다. 그리고 nginx 루트 디렉토리 바로 아래 /www-data/로 부터 프론트엔드 결과물을 띄우고 싶다.

그래서 **location /console** 이렇게 하면 /console로 들어오는 것들이 걸린다. \(여기서 regex 검사도 할 수 있는 듯\)

만약 위의 설정에서 root www-data를 사용한다면 /console/www-data 경로에서 찾을 것이다.

그런데 우리는 바로 루트 디렉토리 아래에 있기 때문에 /console을 alias로 대체해서 /www-data/에서 찾게 해준다.

```text
server {
    listen       8080;
    listen  [::]:8080;
    server_name  localhost;

    location /console {
      alias  /www-data/;
      index  index.html index.htm;

      limit_except GET HEAD POST {
          deny all;
      }
    }

    location /bss {
       # empty
    }

    location / {
      rewrite ^/(.*)$ /console/$1 permanent;
    }
}
```



그리고 만약 사용자가 http://localhost:8080/으로 접속한다면 어떡할까?

에러나 잘못된 리소스를 보여주는 것이 아니라 localhost:8080/console로 redirect 시켜주고 싶다.

이럴 때 rewrite로 해주는 방법이 있다.

/.....로 들어왔을 때 /console/..... 로 path를 rewrite해주고 redirect 시켜주라는 뜻이다. \(permanent\)

그런데 이 때 /bss/로 시작하는 API에는 redirection 되어서 /console/이 앞에 붙으면 안 된다.

그럴 때는 location /bss를 한번 더 걸러주자.

솔직히 잘 모르겠다. regex로 걸러내는 것도 모르겠고 되어야 할 거 같은건 안 되고 안 되어야 할 거 같은게 되고 잘 모르겠다.

참고

* nginx rewrite, redirect 관련
  * [https://lhb.kr/news/article.html?no=3101](https://lhb.kr/news/article.html?no=3101)
  * [https://opentutorials.org/module/384/4337](https://opentutorials.org/module/384/4337)
  * [https://stackoverflow.com/questions/16302897/nginx-location-not-equal-to-regex](https://stackoverflow.com/questions/16302897/nginx-location-not-equal-to-regex)
* \[URL과 URI의 의미와 차이점 \(Difference between URL & URI\)\] [https://blog.lael.be/post/61](https://blog.lael.be/post/61)

