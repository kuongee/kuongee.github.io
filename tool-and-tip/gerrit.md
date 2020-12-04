---
description: gerrit을 사용하면서 새롭게 알게 되고 실수로 잘못 사용했던 부분을 잊지 않기 위해 정리합니다.
---

# \[Gerrit\]으로 코드리뷰하기

## Gerrit 소개

* **Gerrit Code Review for Git**
  * Gerrit document의 메인 타이틀이다.
  * Gerrit은 메인 타이틀에서도 알 수 있듯이 코드 리뷰를 위한 툴이다.
    * Git server의 역할을 한다. 
      * Host Git repositories & web front-end for doing code review
    * 코드 베이스에 추가되기 전, 코드를 리뷰하고 적용할 수 있도록 한다.
  * **Code review**의 중요성을 강조하며 Gerrit을 소개하고 있다.
  * 아래 그림을 보면 코드 리뷰를 위해서 개발자들은 Pending Changes 부분에 코드의 변화를 보낸다. 모든 변화가 확인이 된 후 실제 코드로 포함된다. \(초록색 부분\)

![From gerrit documentation](../.gitbook/assets/image%20%287%29.png)

## 주의할 부분

gerrit에 변화를 업로드할 때 그냥 "git push" 를 하면 안 된다! \(안 그러면 그냥 master로 올라가버리는 일이 생겨버릴 수도 있다.\)

* commit은 반드시 ref로 push 되어야 한다. → refs/for/&lt;target-branch&gt;
  * 바로 repository에 push 되지 않고 code review를 할 수 있도록 받아준다.
  * 참고로 단순히 git push를 했을 때 아무런 메시지 없이 바로 target-branch에 포함되어버린다.

```bash
$ git commit
$ git push origin HEAD:refs/for/master
```

* 각 commit이 들어오면 Gerrit 내부에서 refs/changes/ namespace 아래에 새로운 브랜치를 생성한다.
* Change에는 Change-Id, meta data, patch set, comments, votes가 포함되어 있다.
  * patch set 중 가장 최근에 승인된 것만이 target branch에 적용된다.
  * Change-Id 는 Gerrit에서 중요!하다. 특히 git commit --amend를 사용할 때.
  * git commit --amend를 호출하면 SHA-1의 값이 변하기 때문에 이것을 사용해서 git commit --amend로 들어온 것을 잡아낼 수가 없다. 따라서 Change-Id라는 것을 부여한다. commit message 하단에 적혀있다. Change-Id를 이용해서 커밋이 amend로 들어온 것인지를 확인한다.

## git ref란?

​commit의 SHA-1 값 정보를 이용해서 history를 볼 수도 있지만 너무 길고 기억하기 어렵기 때문에 reference / refs라는 간단한 이름을 사용한다.

[https://git-scm.com/book/en/v2/Git-Internals-Git-References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)

## Reference

[https://gerrit-review.googlesource.com/Documentation/intro-user.html](https://gerrit-review.googlesource.com/Documentation/intro-user.html)

