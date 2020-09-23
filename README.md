# prettier-eslint-example

prettier-eslint の素振り

## わざと矛盾した設定ファイルを作る

.eslintrc.js

```js
module.exports = {
  env: {
    browser: true,
    es2021: true
  },
  extends: ['eslint:recommended', 'plugin:@typescript-eslint/recommended'],
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaVersion: 12,
    sourceType: 'module'
  },
  plugins: ['@typescript-eslint'],
  rules: {
    quotes: ['error', 'double']
  }
};
```

シングルがエラーになる設定

FYI: https://eslint.org/docs/rules/quotes#double

.prettierrc.js

```js
module.exports = {
  singleQuote: true
};
```

## 対象

```
throw { a: "1" };
```

## コマンドを叩く

```
npm run format
```

prettier で定義した single quote ではなく、eslint で設定した double が優先される。

=> この状態で lint を実行すると eslint は落ちない。
