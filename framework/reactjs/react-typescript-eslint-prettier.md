# React - Typescript eslint, prettier 개발 환경 구축

{% hint style="info" %}
CRA Typescript Template eslint, prettier 개발 환경 구축
{% endhint %}

* [CRA(create-react-app) 시작하기](react-typescript-eslint-prettier.md#cra-create-react-app)
* [절대경로 alias 설정](react-typescript-eslint-prettier.md#alias)
* [ESLint와 Prettier](react-typescript-eslint-prettier.md#eslint-prettier)
* [ESLint airbnb style 적용](react-typescript-eslint-prettier.md#eslint-airbnb-style)
* [Testing Library 설정](react-typescript-eslint-prettier.md#testing-library)



## CRA(create-react-app) 시작하기

`npm`으로 시작하기

```bash
npx create-react-app {프로젝트이름} --template typescript
```



`yarn`으로 시작하기

```bash
yarn create react-app {프로젝트이름} --template typescript
```



## 절대경로 alias 설정

1. tsconfig.json의 `compilerOptions` > `baseUrl`, `paths` 속성 추가&#x20;

```json
// tsconfig.json
{
  "compilerOptions": {
    ...
    "baseUrl": "./src",
    "paths": {
      "@/*": ["*"] // src/App.tsx는 @/App.tsx로 경로 설정
    },
    ...
  }
}
```



2. webpack 구성 커스터마이징 위해 `craco` 설치, craco.config.js에 alias 추가

{% hint style="info" %}
웹팩 커스텀하지 않으면 IDE에서는 인식하지만 브라우저에서 인식못함.
{% endhint %}

```bash
# npm
npm install -D @craco/craco

# yarn
yarn add -D @craco/craco
```



```javascript
// craco.config.js
module.exports = {
  webpack: {
    alias: {
      '@': path.resolve(__dirname, 'src/'),
    },
  },
}
```



## ESLint와 Prettier

1. `ESLint`, `Prettier` 설치

```bash
# npm
npm install -D eslint prettier

# yarn
yarn add -D eslint prettier
```

2. `Prettier`가 적용하는 코드 스타일과 중복되는 `ESLint` 규칙을 비활성화하여 충돌 방지

```bash
# npm
npm install -D eslint-config-prettier eslint-plugin-prettier

# yarn
yarn add -D eslint-config-prettier eslint-plugin-prettier
```

3. `TypeScript` `ESLint` parser & plugin

```bash
# npm
npm install -D eslint-config-prettier eslint-plugin-prettier

# yarn
yarn add -D @typescript-eslint/parser @typescript-eslint/eslint-plugin
```

4. `ESLint`에서 `TypeScript` 모듈을 불러올 때 경로를 지정해주는 도구(default가 js이기 때문)

```bash
# npm
npm install -D eslint-import-resolver-typescript

# yarn
yarn add -D eslint-import-resolver-typescript
```

4. .eslintrc.json

```json
{
  "env": { "node": true, "browser": true },
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint", "prettier"],
  "extends": [
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "rules": {},
  "settings": {
    "import/parsers": {
      "@typescript-eslint/parser": [".ts", ".tsx"]
    },
    "import/resolver": {
      "typescript": {}
    }
  }
}

```

5. .prettierrc.json

```json
{
  "printWidth": 80,
  "singleQuote": true,
  "arrowParens": "avoid",
  "semi": true,
  "useTabs": false,
  "trailingComma": "all",
  "tabWidth": 2
}
```



## \* ESLint airbnb style 적용

1. 패키지 다운로드

```bash
# npm
npm install -D eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks

# yarn
yarn add -D eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks
```

2. .eslintrc.json 수정

```json
{
  "env": { "node": true, "browser": true },
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint", "prettier"],
  "extends": [
    "airbnb",
    "airbnb/hooks",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ],
  "rules": {
    "react/jsx-filename-extension": [
      "warn",
      { "extensions": [".js", ".jsx", ".ts", ".tsx"] }
    ],
    "import/no-unresolved": "error",
    "import/extensions": [
      "error",
      "ignorePackages",
      {
        "js": "never",
        "jsx": "never",
        "ts": "never",
        "tsx": "never"
      }
    ]
  },
  "settings": {
    "import/parsers": {
      "@typescript-eslint/parser": [".ts", ".tsx"]
    },
    "import/resolver": {
      "typescript": {}
    }
  }
}
```



## Testing Library 설정

Jest 기준으로 절대 경로 alias 반영

```javascript
// craco.config.js
module.exports = {
    ...
    jest: {
        configure: {
          moduleNameMapper: {
            '^@/(.*)$': '<rootDir>/src/$1',
          },
        },
    },
    ...
}
```
