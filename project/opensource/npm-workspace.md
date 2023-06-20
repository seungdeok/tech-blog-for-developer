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



### Workspace 추가

Workspace의 create 명령어로 packages 디렉터리에 추가할 수 있다.

```bash
$ npx learn create {패키지 이름}
```



Workspace의 의존성도 create로 추가할 수 있다.(scope 옵션으로 전역/특정 패키지 여부를 결정한다)

> 의존성은 오픈 소스 라이브러리일 수도 있지만 내부 workspace일 수도 있다 말 그대로 의존성!

```bash
$ npx learn add {의존성 이름}
$ npx learn add {의존성 이름} --scope={패키지 이름}
$ npx learn add {의존성 이름} --ignore-workspace-root-check
```

* `ignore-workspace-root-check` 옵션은 루트에만 설치!



### Learn Script

Learn에서 지원하는 다양한 스크립트가 있지만 주로 쓰는 script만 우선 정리해본다!!

다른 스크립트는 [공식 문서](https://lerna.js.org/docs/api-reference/commands)를 참조해보자!



`learn run {npm script}`: 모든 workspace의 npm script 수행

`learn exec -- {CLI 명령어}`: 모든 workspace의 CLI 명령어 수행

`learn publish`: 모든 workspace의 변경된 패키지 publish

`lerna version`: workspace 버전 자동 상승 + git tag + CHANGELOG





### 출처

* [https://docs.npmjs.com/cli/v7/using-npm/workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces)
* [https://d2.naver.com/helloworld/7553804](https://d2.naver.com/helloworld/7553804)
