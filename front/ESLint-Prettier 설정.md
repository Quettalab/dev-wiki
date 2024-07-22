## ESLint/Prettier 설정

- ESLint란 소스 코드를 분석하여 프로그램 오류, 버그, 스타일 오류를 잡아주는 Javascript Linter이다.

### ESLint Style Guide
- ESLint Style Guide 중 많은 개발자가 사용하고 있는 것은 에어비엔디와 구글이다.
- Air BnB
  - 코딩 스타일: Airbnb의 스타일 가이드는 매우 엄격하며, 코드 품질과 일관성을 중시한다. 더 많은 규칙이 있으며, 더 많은 베스트 프랙티스를 포함한다.
  - 주요 특징:
    - 2칸 또는 4칸 들여쓰기 (팀 내에서 결정 가능)
    - 세미콜론 사용
    - 작은 따옴표(') 사용
    - 객체와 배열의 트레일링 쉼표(trailing commas)를 사용
    - 함수 선언 시 공백을 많이 사용하여 가독성을 높임
    - 변수 선언 시 const와 let을 사용하고, var를 사용하지 않음
    - 화살표 함수 사용을 장려함
- Google
  - 코딩 스타일: Google의 스타일 가이드는 상대적으로 간결하고 단순하다. 읽기 쉽고 유지보수하기 쉬운 코드를 지향하며, 엄격하지 않은 편이다.
  - 주요 특징:
    - 2칸 들여쓰기
    - 세미콜론 사용
    - 작은 따옴표(') 대신 큰 따옴표(") 사용
    - 객체와 배열의 트레일링 쉼표(trailing commas)를 허용하지 않음
    - 함수 선언 시 공백을 최소화함
- 결론 : Node JS로 개발은 처음이므로 덜 엄격한 구글 스타일 가이드를 사용하고, 추후 어느정도 숙련이 되었을 때, 우리만의 규칙을 정해서 리팩토링하는 것이 좋아보임.

### ESLint 설정법
1. ESLint, Google Style Guide 설치
```bash
npm install eslint@8 eslint-config-google@latest --save-dev
```
2. ESLint Config 파일 생성
- 루트 디렉토리에 `.eslintrc.js` 파일 생성 후, 아래 코드 추가
```javascript
module.exports = {
  env: {
    node: true,
    es2021: true,
  },
  extends: ['eslint:recommended', 'google'],
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
  },
  rules: {
    'indent': ['error', 2],
    'linebreak-style': ['error', 'unix'],
    'quotes': ['error', 'single'],
    'semi': ['error', 'always'],
  },
};
```
3. package.json 에 아래 코드를 추가하여 규칙을 쉽게 추가하거나 수정할 수 있다.
```json
"scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
}
```
4. 린팅 명령어
- 해당 명령어를 통해서 규칙에 위반되는 코드를 확인할 수 있다.
```bash
npm run lint 
```

### Prettier 설정법
1. Prettier와 관련된 패키지 설치
```bash
npm install --save-dev prettier eslint-config-prettier eslint-plugin-prettier
```
2. `.prettierrc` 파일 생성 후, 내용 추가
```json
{
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 100,
  "tabWidth": 2,
  "semi": true
}
```
3. `.eslintrc.js` 파일 수정
```javascript
module.exports = {
  ...
  
  extends: [
    'eslint:recommended',
    'google',
    'plugin:prettier/recommended',  // 이 줄 추가
  ],
  
  rules: {
    // ESLint 규칙 중 Prettier와 충돌할 수 있는 규칙들은 비활성화
    'indent': 'off',
    'object-curly-spacing': 'off',
    'comma-dangle': 'off',
  },
  
  ...
};
```
4. `package.json`에 코드 추가
```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix",
  "format": "prettier --write ."  // 이 줄 추가
}
```