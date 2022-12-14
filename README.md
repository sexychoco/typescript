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
![image](https://user-images.githubusercontent.com/95459711/182028211-1d72eae0-e3e2-4b4a-8f2c-58e231ddc171.png)
타입스크립트(Typescript)란 자바스크립트의 단점을 보완하기 위해 만들어진 **오픈소스 프로그래밍 언어**다. 자바스크립트는 동적 타입 언어이기 때문에 런타임 오류가 발견될 가능성이 크다. 그러나 타입스크립트는 코드 작성 단계에서 타입을 선언해주기 때문에 런타임 오류를 방지할 수 있어  위와 같은 자바스크립트의 단점을 보완해준다. 물론, 타입스크립트 또한 매번 타입을 선언해주어야 하기 때문에 코드 작성 시 번거로움이 있을 수 있으며, 컴파일 시간이 증가한다는 단점이 있다.

#### 자바스크립트 슈퍼셋 (Javascript + α )
![image](https://user-images.githubusercontent.com/95459711/182028234-6eca139d-25e8-401d-af09-fc2335a503a7.png)
타입스크립트는 자바스크립의 슈퍼셋이다. 즉, 자바스크립트를 확장한 언어이기도 하며, ECMA 표준을 따르기 때문에 ES6 문법을 포함하고  클래스, 인터페이스와 같은 객체 지향 프로그래밍 패턴을 제공하고 있다. 

#### Call Signature
Call Signature란 함수의 매개변수와 반환 값의 타입을 미리 선언하는 것을 의미한다. 
```typescript
type Add = (a:number, b:number) => number;

const add:Add = (a,b) => a+b
```
#### Polymorphism , Generic
poly(많은) + morphism(구조) ⇒ 함수의 다형성을 의미한다. 보다시피 아래의 SuperPrint 함수는 boolean 이나 number 로 이루어진 배열을 가지고 있으므로 여러 형태를 가지고 있다고 할 수 있으며 이것이 바로 함수의 다형성이다. 
```typescript
type SuperPrint = {
		(arr:number[]):void
		(arr:boolean[]):void
		(arr:string[]):void
}

const superPrint : superPrint = (arr) => {
		arr.forEach(i => console.log(i))
}

superPrint([1,2,3,4])
superPrint([[true,False,true])
```
여기서 concrete type 이란 number,boolean,string 와 같은 타입을 의미한다.  위에서와 같이 타입을 선언했으나, 만약 내가 여러 데이터의 타입을 섞어서 적용시키고 싶다면 Call signature 조합을 하나하나 해줄 것이 아니라 generic 을 사용한다. generic 은 아래와 같이 <TypePlaceholder> 를 붙여줌으로써 다음과 같이 사용할 수 있다.generic 을 사용하면 우리가 직접 데이터의 타입을 선언하는 것이 아니라 타입스크립트가 직접 타입을 알아내 적용한다.

```typescript
type SuperPrint = {
		<TypePlaceholder>(arr:TypePlaceholder[]):void
}

const superPrint : superPrint = (arr) => {
		arr.forEach(i => console.log(i))
}

superPrint([1,2,3,4])
superPrint([[true,False,true])
```

**그렇다면 Generic 대신 any 를 사용해도 되지 않는가?**  
any 를 사용하게 된다면 모든 데이터의 타입은 any 로 선언되기 때문에 더 이상 보호받지 못하고 에러를 유발할 수 있다.

#### Type, Interfaces
타입스크립트에게는 오브젝트의 모양을 알려주는 2가지 방법이 있으며, Type, Interface 가 이에 해당한다. 
먼저, Types 은 매우 다재다능한 키워드이다. 타입 alis 를 만들거나 특정 값을 지니도록 제한, 또는 오브젝트 모양을 묘사하는데 쓰인다. 
```typescript
type Team = "red" | "blue" | "yellow"
type Health = 1 | 5 | 10

type Player = {
	nickname:string,
	team: Team,
	health: Health
}

const nico : Player = {
	nickname: "nico",
	team: "yellow",
	health: 10,
}
```
이 코드를 보면 Team 을 "red","blue" 혹은 "yellow" 로만 제한할 수 있다. 
오브젝트의 형태를 묘사하는 또 다른 방법에는 interface 가 있다. 
```typescript
type Team = "red" | "blue" | "yellow"
type Health = 1 | 5 | 10

interface Player = {
	nickname:string,
	team: Team,
	health: Health
}

const nico : Player = {
	nickname: "nico",
	team: "yellow",
	health: 10,
}
```
위의 코드와 크게 다른 점은 없다. interface는 오직 한가지 용도만을 가지고 있고 그건 오브젝트 모양을 특정해주기 위한 것이다. 

