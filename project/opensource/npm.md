# NPM 배포하기

개발자들에게 오픈소스는 뗄 수 없는 관계인 것 같다.

누구나 기여할 수 있는 오픈소스로의 배포방법을 정리하고자 한다.



### NPM

Node.js의 기본 패키지 매니저이며 비교적 최근에 나온 yarn, pnpm도 npm이 시초였다.

[Node.js](https://nodejs.org/en)를 설치하면 npm이 같이 설치된다.

한 번쯤은 [npmjs.com](https://npmjs.com)에서 오픈소스를 검색하여 설치해본 경험이 있을 것이라 생각하고 진행해보겠다.



### 패키지 개발

1. 폴더를 생성하고 내부 터미널에서 npm 초기화한다.

```bash
$ npm init -y
```



2. CLI 인터페이스 패키지의 도움을 받기 위해 Dependencies 설치

```bash
$ npm install commander
```



3. 패키지에서 동작시킬 js파일을 만든다.

{% code title="bin/index.js" %}
```javascript
#!/usr/bin/env node

const { program } = require('commander')

function init() {
    console.log('init project');
}

program.action(args => {
    init();
});

program.parse(process.argv);
```
{% endcode %}

* `#!/usr/bin/env node` : 시스템에게 해당 파일을 node 인터프리터로 실행할 것을 명시
* 실행되면 program의 action부분이 실행되어 init이라는 함수가 동작하게 됩니다.



4. 마지막으로 package.json으로 배포 정보와 대상을 지정해줍니다.

```json
{
  "name": "npm-release-version",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "bin": {
    "npm-release-version": "./bin/index.js"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "commander": "^11.0.0"
  }
}

```

* name과 version 등은 배포 정보로 쓰인다.
* bin은 실행할 수 있는 패키지를 알려주고 해당 파일의 Symlink를 생성한다. (+ npm-release-version은 CLI 명령어로 쓰임)



### 개발버전 사용

로컬에서 사용하는 방법은 global에 Symlink로 연결하면 된다.

```bash
$ npm link
$ npm-release-version
```

혹은&#x20;

```bash
$ npm install -g
$ npm-release-version
```



global 링크가 걸려있는지 체크 후

```bash
$ npm ls -g --depth=0
```

삭제는 해당 패키지를 uninstall하면 된다.

```bash
$ npm uninstall npm-release-version -g
```



### 배포

> 회원가입이 안되어있다면 [회원가입](https://npmjs.com) 부터!

로그인

```bash
$ npm login
```

로그인 확인

```bash
$ npm whoami
```



패키지명이 중복되면 등록이 안되기 때문에 검색해서 체크해줘야 합니다.

1. 사이트 내 검색

{% embed url="https://www.npmjs.com/" %}

2. CLI

```bash
$ npm info {패키지 이름}
```



정상적으로 여기까지 왔다면 배포를 만끽하자

```bash
$ npm publish
```



{% hint style="info" %}
혹여 삭제하고 싶다면 아래 명령어를 72시간 내로 사용하자!

`npm unpublish {패키지 이름} -f`
{% endhint %}



### 배포버전 사용

> 개발버전을 전역에서 삭제하고 다시 설치하자

전역으로 설치하는 방법

```bash
$ npm install {패키지 이름} -g
```



`npx`를 사용하는 방법

```
$ npx {패키지 이름} -g
```

### 버전 업데이트

버전을 업데이트할 때는 pacakge.json의 version 코드를 올려주고 다시 배포하자!

```bash
$ npm publish
```





