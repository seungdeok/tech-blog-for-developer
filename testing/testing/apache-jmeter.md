# Apache JMeter

성능테스트 중 부하테스트(Load Test) 도구를 찾고 있었고 아래의 기준으로 선택하였다.

* [x] 타 직군도 사용하기 위해 GUI가 존재해야한다.
* [x] HTTP 테스트가 가능해야 한다.
* [x] 시나리오 테스트가 가능해야 한다.
* [x] (선택적)오픈소스여야 한다.

`JMeter` vs `Locust` 중 GUI에 더 친화적인 `JMeter`를 선택하였다.



## Installment.

1. brew에서 설치 (Windows는 [여기서](https://jmeter.apache.org/download\_jmeter.cgi))

```bash
# intel
brew install jmeter
# apple silicon
arch -arm64 brew install jmeter
```

2. 실행

```bash
# intel
open /usr/local/bin/jmeter
# apple silicon
open /opt/homebrew/bin/Jmeter
```



## Useage.

1. Options > Plugin Manager > install packages
   1. `3 Basic Group`: 여러 개의 스레드 그룹을 묶어서 실행하고 관리 가능
   2. `Custom Thread Groups`: 사용자 정의 스레드 그룹을 생성하고 사용 가능
   3. `JMeter Listener pack`: 테스트 결과를 시각적으로 분석하고 모니터링 가능
2. Test Plan > Add > Threads(Users) > Thread Group
3. Thread Group > Add > Sampler > HTTP Request
   1. IP, Port, Arguments를 입력
   2. Start Button
4. Thread Group > Add > Listener > Summary Report
5. Thread Group > Add > Listener > View Result Tree
6. Thread Group > Add > Listener > Transactions per Second



## Next Step.

생각보다 강력한 플러그인들을 지원하였고

다양한 프로토콜을 지원하고 Desktop용 GUI를 지원해줘 사용성도 훌륭했다.

다만, 스크립트 코드에 대한 러닝커브가 존재하여 시나리오를 짜기위한 공부가 필요하다.



