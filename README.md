## TypeScript BLockChain
Make BlockChain with Typescript

### Description
Typescript 를 통해 어떻게 코드를 개선하고, 버그를 방지할 수 있는지 학습하였습니다. 

### Theory 
* Types
* Interfaces
* Classes
* Polymorphism
* Generics
* Call Signatures

### Packages
* Typescript
* TSConfig
* TSNode

### 타입스크립트란?
타입스크립트(Typescript)란 자바스크립트의 단점을 보완하기 위해 만들어진 오픈소스 프로그래밍 언어다. 자바스크립트는 동적 타입 언어이기 때문에 런타임 오류가 발견될 가능성이 크다. 그러나 타입스크립트는 코드 작성 단계에서 타입을 선언해주기 때문에 런타임 오류를 방지할 수 있어  위와 같은 자바스크립트의 단점을 보완해준다. 물론, 타입스크립트 또한 매번 타입을 ###선언해주어야 하기 때문에 코드 작성 시 번거로움이 있을 수 있으며, 컴파일 시간이 증가한다는 단점이 있다.

#### 자바스크립트 슈퍼셋 (Javascript + α )
타입스크립트는 자바스크립의 슈퍼셋이다. 즉, 자바스크립트를 확장한 언어이기도 하며, ECMA 표준을 따르기 때문에 ES6 문법을 포함하고  클래스, 인터페이스와 같은 객체 지향 프로그래밍 패턴을 제공하고 있다. 

#### Call Signature
Call Signature란 함수의 매개변수와 반환 값의 타입을 미리 선언하는 것을 의미한다. 
```typescript
type Add = (a:number, b:number) => number;

const add:Add = (a,b) => a+b
```
