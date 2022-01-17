# Micro FE에서 네비게이션 가드

AppManager에서 navigation guard가 route 변경을 감지하지 못하는 문제 해결

기존 beforeRouteEnter로만 변경을 감지하고 있는데 같은 컴포넌트를 사용하는 path의 경우 변경을 감지하지 못하고 있음

* /main → /main/micro-poc : beforeRouteEnter에서 변경 감지
* /main → /main/aui-sample : beforeRouteEnter에서 감지 하지 못함\


```
// routes.js
{
    path: '/main',
    component: Main,
    children: [
      { path: '', component: Dashboard },
      { path: '*', component: AppManager }, // /main/* 은 AppManager를 공통으로 사용해서 그런 것 같음
    ],
},
```

그래서 컴포넌트가 재사용 될 때는 다른 가드를 사용하여 업데이트를 감지해야함

[https://router.vuejs.org/guide/advanced/navigation-guards.html](https://router.vuejs.org/guide/advanced/navigation-guards.html)\


beforeRouteUpdate (2.2 버전에 추가)

해당 컴포넌트에 변경이 생겼을 경우 불림

예를 들어 /foo/:id 로 라우트 되는 경우 /foo/1와 /foo/2는 같은 컴포넌트 인스턴스가 재사용되는데 이 때 이게 호출되는 것

여기서는 this로 컴포넌트 인스턴스에 접근이 가능

※ next() 콜백

beforeRouteEnter만 next의 콜백을 지원한다고 함 (지원하는 이유: navigation이 확정된 다음에 그려지기 때문에 생성되기 때문에 this로 접근할 수가 없음, 그래서 콜백을 넘겨서 접근할 수 있게)

beforeRouteUpdate나 beforeRouteLeave는 이미 this를 사용할 수 있기 때문에 콜백을 보낼 필요가 없어서 지원도 안 하고 있음
