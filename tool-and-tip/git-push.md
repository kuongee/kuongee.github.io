# \[Git\] push

리모트 저장소에 로컬 저장소 변경 내용을 push 하기

git push {리모트 저장소 이름} {브랜치 이름}  
예시: git push origin master



{repo}/.git/config에 git push 설정을 추가할 수 있다.

```bash
# .git/config 내용

[remote "abc"]
	url = ssh://....
	push = {branch_name}
------------------------------------	
$ git push abc
```



