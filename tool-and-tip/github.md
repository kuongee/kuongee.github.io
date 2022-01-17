---
description: remote 개념 이해하기
---

# \[Github]으로 협업하기

![](<../.gitbook/assets/image (5).png>)

Owner의 A-Repo에 나도 작업해서 올리고 싶을 때:

1. Owner의 repository를 fork 한다. (github 상에서 버튼 클릭으로 가능)
2. fork 해온 repository를 나의 local로 clone 해온다.\
   remote repository의 주소는 너무 길어서 단축이름이 생기는데 기본적으로 origin 이라고 결정된다.&#x20;
3. Owner의 repository의 정보도 아래와 같이 설정한다.\
   git remote add \[단축이름] \[owner's repo addr]\
   ex) git remote add upstream https://github.com/Owner/A-Repo
4. 내가 작업하는 도중 Owner 쪽에서 생긴 변경을 가져와야 한다. (2가지 방법)
   1.

       `git stash // 나의 변경 내용 임시 저장`\
       `git pull --rebase upstream master // Owner의 master branch의 내용을 가져와서 rebase`\
       `git stash pop`\
       `....`&#x20;
   2.

       `git fetch upstream // Owner의 repository 변경 내용만 가져온다.`\
       `git rebase upstream/master`
5. 변경 내용을 가져온 뒤 내가 고친 내용과 conflict가 나면 처리하고 나의 remote repository에 push 한다.
6. github에서 pull request를 보내준다.\


