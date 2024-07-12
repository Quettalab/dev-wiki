## ESLint/Prettier 설정

- ESLint란 소스 코드를 분석하여 프로그램 오류, 버그, 스타일 오류를 잡아주는 Javascript Linter이다.

### ESLint 설정법
1. ESLint 초기화
```bash
npm install eslint --save-dev
```
2. ESLint Config 파일 생성
```bash
npx eslint --init
```
3. 자신의 프로젝트에 맞게 질문 답하기
```
// core-api의 eslint 설정
✔ How would you like to use ESLint? · problems
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · none
✔ Does your project use TypeScript? · javascript
✔ Where does your code run? · browser

The config that you've selected requires the following dependencies:

eslint@9.x, globals, @eslint/js
✔ Would you like to install them now? · No / Yes
✔ Which package manager do you want to use? · npm
```
4. 위 과정을 완료하면 루트 디렉토리에 `eslint-config.mjs`파일이 생성된다. 해당 파일에 설정을 하면 된다.