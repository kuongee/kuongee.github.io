# 구현하면서 배운 점

gerrit

* git push origin HEAD:refs/for/customBuild

git

* git reset HEAD\~2
* git stash
*
  * remote에 새로 올라온 패치를 받기 전에 내가 작업하던 거 잠시 저장해두고 패치를 받는다.

grunt file

javascript library 빌드 과정

* decomment: javascript 소스코드 comment 제거
* concat: 코드 한꺼번에 묶기
* uglify
* cssmin
* copy
* compress

javascript object가 argument로 넘어올 때

* pass by value\

  * string/number
* pass by reference
  * object랑 array.
  * reference로 넘어온 애들은 함수 안에서 변경이 생기면 그대로 변경
* [https://medium.com/nodesimplified/javascript-pass-by-value-and-pass-by-reference-in-javascript-fcf10305aa9c](https://medium.com/nodesimplified/javascript-pass-by-value-and-pass-by-reference-in-javascript-fcf10305aa9c)

javascript undefined

javascript deep copy / shallow copy

* \= 를 이용하면 reference가 전달
* [https://we-are.bookmyshow.com/understanding-deep-and-shallow-copy-in-javascript-13438bad941c](https://we-are.bookmyshow.com/understanding-deep-and-shallow-copy-in-javascript-13438bad941c)

ESLint / prettier\
