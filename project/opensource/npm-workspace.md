# NPM Workspace

멀티 레포로 운영했을 때의 동기화 문제를 NPM Workspace로 해결하고자 한다.

많은 기업에서 workspace를 활용한 모노레포 방식을 채택하고 있고

무조건적인 정답은 아니지만 같은 도메인에서 동기화 문제에서는 최적의 솔루션으로 쓸 수 있다고 생각한다.

개인 프로젝트 중 CLI 프로젝트에서 템플릿을 workspace로 관리하는 방식을 적용해보면서 정리하고자 한다.



### NPM Workspace

> 단일 최상위 루트 패키지 내에서 로컬 파일 시스템의 여러 패키지 관리를 지원하는 npm cli의 기능 집합을 나타내는 일반적인 용어 (npmjs docs)

[Yarn(1.x)](https://classic.yarnpkg.com/lang/en/docs/workspaces/) 또는 [npm(7.x)](https://docs.npmjs.com/cli/v7/using-npm/workspaces)의 [workspaces](https://yarnpkg.com/features/workspaces) 필드를 사용하면 한 패키지를 루트로 여러 패키지를 관리하기 용이해진다.

{% code title="package.json" %}
```json
{
  ...
  "workspaces": [
    "packages/*"
  ],
  ...
}

```
{% endcode %}

그리고 workspace를 사용해 간단히 [모노레포](https://yarnpkg.com/advanced/lexicon#monorepository)를 구성할 수 있다.&#x20;



### Learn

모노레포 관리 도구로 가장 많은 프로젝트에서 쓰는 `Learn`을 이용해보고자 한다.

`Learn`은 Workspace의 관리, 테스트 , 빌드, 배포 등을 도와준다.



`learn init`으로 프로젝트를 초기화한다.

```
$ npx learn init
```



package.json이 구성되고 workspace 파일을 구성한다.

```json
{
  "name": "root",
  "private": true,
  "workspaces": [
    "packages/*"
  ],
  "dependencies": {},
  "devDependencies": {
    "lerna": "^7.0.2"
  }
}

```



packages 디렉토리 안에 관리할 패키지를 넣어 Workspace를 관리하도록 한다.



{% hint style="info" %}
Learn을 활용한 테스트, 빌드, 배포는 추가로 작성하겠다!(커밍순!)
{% endhint %}



### 출처

* [https://docs.npmjs.com/cli/v7/using-npm/workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces)
* [https://d2.naver.com/helloworld/7553804](https://d2.naver.com/helloworld/7553804)
