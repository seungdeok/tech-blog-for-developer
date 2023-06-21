---
description: 'feat: ReactJS'
---

# 바닐라 JS 웹 컴포넌트 개발기

## 초기 세팅.

### 컴파일러 세팅

> Babel을 사용함으로 ES6+ 이상의 JS 코드를 하위버전 문법으로 변환시켜주고 ES6+문법을 사용하고자 하였다.

1. Babel packages  설치

```bash
$ npm install --save-dev @babel/cli @babel/core @babel/node @babel/preset-env @babel/polyfill
```



2. `babel.config.json`

```json
{
  "presets": ["@babel/preset-env"]
}
```



### Local Server

1. VS Code `Live Server`
2. NPM Package `serve`(**Selected,** VS Code를 사용하지 않는 케이스가 있다고 생각)

## 개발.

### HTML 세팅

HTML파일을 만들고 동적으로 생성할 수 있도록 script 파일을 연결합니다.

{% code title="index.html" %}
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <div class="App"></div>
    <script type="module" src="./src/index.js"></script>
  </body>
</html>
```
{% endcode %}



### Core Component

1. 공통 Component class를 React Lifecycle 기반으로 만듭니다.

* `constructor`: 각 컴포넌트는 target 원소를 가지고 props로 다른 컴포넌트로 내려줄 수 있습니다.
* `setup`: 초기값 지정 initState
* `template`: render의 UI 부분을 담당하여 컴포넌트화 시킬 수 있도록 합니다.
* `setState`: React와 같이 state가 변하면 해당 부분을 찾아 리렌더링을 시킵니다.
* `mounted`: React Lifecycle `componentDidMount`
* `updated`:  React Lifecycle `componentDidUpdate`
* `unmounted`: React Lifecycle `componentWillUnmount`

```javascript
class Component {
  constructor(target, props = {}) {
    this.target = target;
    this.props = props;
    this.setup();
    this.render();
    this.mounted();

    window.onbeforeunload = () => {
      this.unmounted();
    };
  }
  setup() {}
  template() {
    return "";
  }
  render() {
    this.target.innerHTML = this.template();
  }
  mounted() {}
  setState(newState, shouldUpdate = true) {
    let isRerender = false;
    for (const key of Object.keys(newState)) {
      if (this.state[key] !== newState[key]) {
        isRerender = true;
        break;
      }
    }

    if (!isRerender) return;

    this.state = { ...this.state, ...newState };

    if (shouldUpdate) {
      this.render();
      this.mounted();
      this.updated();
    }
  }
  updated() {}
  unmounted() {}
}

export default Component;
```



2. Component를 App.js가 상속받습니다.

```javascript
import Component from "./core/Component.js";

class App extends Component {
  setup() {
    this.state = {
      data: [],
      text: "",
    };
  }

  template() {
    return `
      <div>
        바닐라 JS 웹 컴포넌트 개발
      </div>
    `;
  }

  mounted() {}

  updated() {}
}

export default App;

```

3. App.js를 index.js에서 호출하여 화면에 렌더합니다.

```javascript
import App from "./App.js";

new App(document.querySelector(".App"), {});
```





## Next Step.

* 리렌더링 성능이 좋지 않아 이 부분은 React의 _휴리스틱 알고리즘_ 활용하여 해당 방식을 적용해볼 것이다.
* React hook을 구현하고 class형 컴포넌트를 함수형으로 바꿔볼 생각이다.

