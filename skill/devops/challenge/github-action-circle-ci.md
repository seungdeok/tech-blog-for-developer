# \[회고] Github Action에서 Circle CI로 마이그레이션 제안

{% hint style="info" %}
회고는 프로젝트 단위로 진행되며 [KPT 방법](https://code-artisan.io/retrospective-method-kpt/)으로 진행됩니다.
{% endhint %}



## 프로젝트 시작하며.

### 1. 마이그레이션의 필요성

기존의 CICD의 경우 Github라는 플랫폼 안에서 사용할 수 있는 Github Action을 활용하여 빌드, 배포, 테스트를 자동화하여 사용하고 있었다. \
\
Github 안에서 소스관리와 더불어 전반적인 배포 관리까지 진행할 수 있어 분산되지 않는 이점이 있다고 생각했다.\
\
하지만, 관리하는 프로젝트가 많아지면서, 모든 프로젝트의 진행상황을 공유하는 소통 비용이 발생하게 되고 솔루션이 필요했다.\
\
새로운 솔루션을 자체 제작하는 것보다는 내부 세션에 올라왔던 Circle CI와 비교하여 마이그레이션을 고려해보기로 하였다.



### 2. Github Action vs Circle CI

* 1차 테스트\
  \- 다음과 같은 평가 기준으로 검토한 후 각 부분에 대해서 의견을 공유하였다.
  * Speed(속도) : 빌드 속도가 상대적으로 느린가?
  * Readability(가독성) : UI의 가독성이 좋은가?
  * Learning Curve(학습 비용) : 초심자가 쉽게 학습할 수 있는가?
  * Community size(커뮤니티 활성도) : 이슈가 발생했을 때, 커뮤니티에서 답을 찾을 수 있는가?
  * Stability(안정성) : 서비스 크래시가 발생하는가?
  * Compatibility(호환성) : github와 같이 쓸 수 있는가?



|                    | Github Action | Circle CI |
| ------------------ | ------------- | --------- |
| **Speed**          | Slow          | Fast      |
| **Readability**    | Low           | High      |
| **Learning Curve** | Low           | High      |
| **Community size** | Big           | Small     |
| **Stability**      | High          | High      |
| **Compatibility**  | High          | High      |

* 1차 평가 결과 속도와 가독성 측면에서 Circle CI가 좋은 평가를 받았지만, 아무래도 커뮤니티와 학습비용은 상대적으로 풀어야할 숙제가 되었다.



* 1차 테스트 추가 피드백
  *   가장 큰 마이그레이션 이유로 꼽히는 가독성 문제는 흩어져 있는 레포지토리의 통합 대시보드를 지원해주는 것이 좋은 평가를 받게 되었다.\


      <figure><img src="https://firebasestorage.googleapis.com/v0/b/decaffeine-a86d4.appspot.com/o/table-4.png?alt=media&#x26;token=62359341-ddb6-4fdd-8eb5-ef73723dbff8" alt=""><figcaption><p>출처 Circle CI</p></figcaption></figure>
  * 학습비용 부분은 상대적인 부분이 있지만, [Github Action에서 마이그레이션하는 가이드](https://circleci.com/docs/migrating-from-github/)를 공식문서에서 제공해주고 있었다.&#x20;



* 2차 테스트\
  \- 2차 테스트에서는 속도 테스트를 진행하였다.\
  \- 공식문서에서는 아래와 같이 40%이상 단축할 수 있다고 한다.\
  \- 토이 프로젝트의 Github action 빌드 시간과 Circle CI로 마이그레이션한 후 시간을 비교해보았다.

<figure><img src="https://firebasestorage.googleapis.com/v0/b/decaffeine-a86d4.appspot.com/o/table-5.png?alt=media&#x26;token=0f28507a-d238-4a86-bb9e-ce5e52516523" alt=""><figcaption><p>출처 Circle CI</p></figcaption></figure>

<figure><img src="https://firebasestorage.googleapis.com/v0/b/decaffeine-a86d4.appspot.com/o/table-1.png?alt=media&#x26;token=d7e6d9fd-ad2a-46c3-9704-671fbee55e70" alt=""><figcaption><p>토이 프로젝트 빌드 시간(좌: Github Action, 우: Circle CI)</p></figcaption></figure>

* 2차 테스트 피드백
  * 개발 환경에 따라 차이가 존재하겠지만, 결과적으로 시간이 20%까지 단축된 부분이 만족스러웠다.



## KPT.

### Keep.

* 대시보드로 가독성이 올라가 관리 리소스를 줄일 수 있었다.
* 빌드시간이 단축되어 개발 리소스를 줄일 수 있었다.
* 기술 제안 방식에 대해 템플릿을 만들 수 있었다.

### Problem.

* github action에서 aws s3 배포 template를 써 migration시에 이슈가 발생했다.
* 실제 프로젝트에서 적용시키지 않아 환경 차이가 존재할 수 있다.

### Try.

* github action에서 aws s3 배포 스크립트 마이그레이션 이슈를 해결하기 위해 배포 스크립트를 aws cli를 통해 직접 작성하였다.





## 프로젝트를 마치며.

첫 기술 제안을 통해 제안 포맷부터 수치를 만들기 위한 탐구까지 스스로도 많이 발전한 것 같다.

내부 프로세스와 생산성 개선을 위해 앞으로도 기회가 있다면 제안을 해볼 것 이다.



## Next Step.

우선 내부 기술 인력들에게 피드백을 받을 것이다.

피드백을 통해 내가 놓친 부분과 잘한 부분을 정리하여

토이 프로젝트에서 그치는 것이 아니라 사내 프로젝트에 적용시킬 수 있도록 유의미한 수치들을 만들어볼 생각이다.
