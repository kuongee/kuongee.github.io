# 성능 향상 결과

## 개요 <a href="#id-8" id="id-8"></a>

기존 프리미엄관과 신규 기술 및 설계를 도입한 프리미엄관의 성능을 비교 분석합니다.

## 성능 개선의 필요성 <a href="#id-8" id="id-8"></a>

사용자가 우수한 페이지 경험을 제공하는 사이트를 선호한다는 결과가 있으며, Google 검색 결과 순위를 지정하는 요인으로 페이지 로드 속도, 모바일 친화성과 같은 다양한 환경 기준을 추가했습니다.  ([참고](https://developers.google.com/search/blog/2020/05/evaluating-page-experience))

또한 구매 전환율이 1초마다 25퍼센트의 감소율을 보여주고 있습니다.

개편된 프리미엄관의 성능 개선을 통해 사용자와 서비스 경험에 긍정적인 영향을 미칠 것입니다.

## 성능 향상의 기술 배경 <a href="#id-8" id="id-8"></a>

* 프론트와 백엔드의 분리
* Next.js 프레임워크
  * SSR
  * 이미지 최적화
* React query
  * 데이터 요청/응답 캐싱

## 프론트엔드 성능 측정 기준 <a href="#id-8" id="id-8"></a>

#### 1. 로딩(속도) <a href="#id-8-1." id="id-8-1."></a>

* FCP(First Contentful Paint): 첫 요소가 로드 될 때까지 걸리는 시간
* LCP(Largest Contentful Paint): 주요 콘텐츠가 로드 될 때까지 걸리는 시간

#### 2. 렌더링 (with Web Vital) <a href="#id-8-2.-withwebvital" id="id-8-2.-withwebvital"></a>

* FID(First Input Delay): 사용자의 이벤트를 받고 실제로 처리할 수 있게 될때까지 걸리는 시간을 FID
* CLS(Cumulative Layout Shift): 시각적인 안전성

## 결과 <a href="#id-8" id="id-8"></a>

* 테스트 환경: 운영
* Network Throttling: Download 800 Mbps로 설정
* initial page load
* 테스트 방법: Chrome Performance 탭에서 측정된 값 5개의 평균 기록

![](<../../../.gitbook/assets/image (6).png>)

![](../../../.gitbook/assets/image.png)

![](<../../../.gitbook/assets/image (4).png>)
