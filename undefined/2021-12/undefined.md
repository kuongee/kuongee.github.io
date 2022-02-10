# 개발환경

Yarn 3 버전에서 yarn 1 버전으로 다시 내려가게 되었음

yarn 3는 pnp 방식으로 빨랐지만

next 12와 yarn 3 사이에 이슈가 문제가 있었던 거 같음

다이나믹 import 문제?

yarn 버전을 canary로 올려서 해결 -> 근데 그냥 안정성을 위해 1로 돌아

{% embed url="https://github.com/vercel/swr/issues/1822" %}
swr에서부터 시작
{% endembed %}

{% embed url="https://github.com/yarnpkg/berry/issues/3687" %}
