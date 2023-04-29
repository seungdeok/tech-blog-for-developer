---
cover: ../../.gitbook/assets/react.png
coverY: 0
---

# \[회고] CRA 없이 React 개발환경 구축

{% hint style="info" %}
회고는 프로젝트 단위로 진행되며 [KPT 방법](https://code-artisan.io/retrospective-method-kpt/)으로 진행됩니다.
{% endhint %}



## 프로젝트 링크.

[https://github.com/seungdeok/react-without-cra](https://github.com/seungdeok/react-without-cra)



## 프로젝트를 시작하며.

Webpack, Babel 그리고 CRA에서 지원해주는 당연시 여기는 기능들을 정리하며&#x20;

CRA없이 커스텀 개발환경 구축을 하기 위한 첫 프로젝트로 시작했다.



## KPT.

### Keep.

* Webpack 세팅과 Babel 세팅 보일러 플레이트를 만들어 다른 프로젝트에서 사용할 수 있을 것 같다.

### Problem.

* 실제 CRA에서는 지원해주는 Testing, ESLint과 같은 개발 생산성을 도와주는 도구들이 있는데 추가 작업이 필요할 것 같다.
* Webpack 세팅을 보일러 플레이트로 만들었지만, 다른 프로젝트에서도 사용할 수 있도록 리팩토링이 필요하다.

### Try.

* CRA에서 지원해주는 다른 도구들도 추가 작업을 할 예정이다.
* Webpack에 대한 공부를 다시해보고 다른 프로젝트에서 쓸 수 있도록 리팩토링을 할 예정이다.



## 프로젝트를 마치며.

가장 많이 쓰는 라이브러리인데 실제로 안다고 생각했던 부분들을 헤매며 작업을 하느라 진땀을 뺐다.

CRA와 같은 kit가 나왔을 때 내가 편한 방법으로만 쓰다보니 이지경(?)이 되지 않았나싶은 생각도 들고

"내가 불편해야 사용하는 사람이 편하다"는 말을 어디선가 들었던 것 같은데 개발도 내가 귀찮더라도

뜯어보는 작업이 필요한 것 같다.



## Next Step.

커스텀 개발 환경 구축의 첫 단추를 끼워넣었다고 생각한다.

두 번째로 이 코드를 베이스로 CRA와 같은 kit를 만들어볼 생각이다.



물론 토이 프로젝트용이 될 수 있겠지만,

내가 쓰는 기술을 직접 만들어보며 Row Level로 내려가보며 제작자의 의도를 이해하는 것이

해당 기술 이해에 가장 빠른 방법이 될 것 같다.
