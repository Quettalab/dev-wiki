# Javascript VS Typescript

## Overview
javascript와 typescript의 차이점은 타입이 없냐 있냐의 차이다.  
type은 우리가 스프링을 사용하면서 매번 사용했던 type을 말한다.  
ex) 사용법 예시  
javascript
```
const a = 3;
const b = 4;
const c = a + b;
```
typescript
```
const a:number = 3;
const b:number = 4;
const c:number = a+b;
```
두 가지 방법에 대한 장점을 알아보고 어떤 언어를 사용할 지 생각해보자

## Javascript의 장점
장점 1 - 유연성
```
let variable = 5;          // 숫자
variable = "Hello";        // 문자열로 변경 가능
variable = { key: "value" }; // 객체로 변경 가능
```
위 코드처럼 변수 타입을 자유롭게 변경할 수 있어 다양한 상황에서 사용하기 편하다.  
  
장점 2 - 생산성
유연하다는 것은 생산성이 빠르 다는 것이다. 이것이 가능한 이유도 타입이 없기 때문이다. 타입이 없으므로 자유롭게 작성이 가능하고 타입에 대한 제약이 없기에 코드도 짧아지게 된다.

## Typescript의 장점
장점 1 - compile에러  
typescript를 사용하면 컴파일에러를 감지한다. javascript에서는 런타임에러로 찾을 수 밖에 없다.
```
function divide(a: number, b: number): number {
    return a / b;
}

divide(10, 2);  // 정상 작동
divide("10", 2);  // 컴파일 에러: Argument of type 'string' is not assignable to parameter of type 'number'.
divide(10, 0);  // 컴파일은 통과하지만, 런타임 에러 발생 가능성 있음
```
  
장점 2 - 가독성  
typescript는 자료형을 명시함으로 어떤 데이터 형식이 들어가 있는지 어떤 데이터의 형식이 return 되는지 알 수 있다. 
javascript의 경우 설명이 되어 있지 않거나 메서드명이 애매할 경우 직접 코드를 보면서 찾을 수 밖에 없다.  
typescript는 interface로 type을 선언해서 사용할 수 있기 때문에 javascript에 비해 파악이 쉽게 가능하다.

## 결론
두 가지 방법에 대한 차이점은 명확하다. javascript는 동적 타입, typescript는 정적타입이라는 것  
두가지 중 어떤한 방식을 선택할 건지는 주관적으로 보인다. 하지만 개인적으로는 java에 익숙해져서 그런지 코드가 길어지더라도 typescript가 더 정감이 간다. 프로젝트가 점점 더 확장되어 갔을 때 더욱 명확하게 장점이 나타날 것 같다.  
물론 javascript도 네이밍을 잘 하고 팀원 간 규칙을 잘 정하면 유연하고 빠른 개발을 할 수 있을 것 같다. 하지만 이런 규칙을 잘 정하더라도 항상 실수하기 마련이라 생각해 유연성을 제한한 typescript가 더 괜찮다고 생각한다.
