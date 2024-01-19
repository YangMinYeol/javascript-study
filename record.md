## 기본 용어

#### Hoisting(호이스팅)

- 인터프리터가 코드를 실행하기 전에 함수, 변수, 클래스 또는 임포트(import)의 선언문을 해당 범위의 맨 위로 끌어올리는 것처럼 보이는 현상

#### Heap(힙)

- 객체, 배열, 함수와 같이 크기가 동적으로 변할 수 있는 참조타입 값을 저장하는 곳

#### Call stack(콜 스택)

- 원시타입 값과 함수 호출의 실행 컨텍스트를 저장하는 곳

## 타입과 변수/상수

1. undefined는 정의되지 않은걸 뜻하므로 undefined로 정의하는일은 없어야 한다.
2. 배열과 객체는 동등연산자(==)와 일치연산자(===)로 비교해도 false가 나온다.
3. Falsy와 Truthy란 false와 true에 역할을 하는 값
   1. Falsy: 0, Nan, false, null, undefined, ""
   2. Falsy 이외에는 모두 true
4. 대문자 상수란 기억하기 힘든값을 별칭으로 빼서 사용할 경우 사용
   1. 값보다 상수를 이용하는것이 오타를 낼 확률이 낮다. 값보다 상수가 훨씬 유의미하다.
   2. 코드 가독성이 좋아진다.
5. Rest 매개변수
   1. 정해지지 않은 수의 매개변수를 배열로 받는다.
   2. 마지막 매개변수에서만 사용 가능하다.

## Error

1. error를 핸들링 하기 위해 try-catch문을 통해 감싸는데 try는 문제가 발생할 수 있는 로직 catch는 문제에 대한 처리 로직
   > 기본적인 에러는 디버깅과 논리적 구조를 통해 해소해야한다. try-catch문으로 전체 스크립트를 감싸는 일은 코드자체, 성능적으로도 안좋은 습관이다.
2. finaly는 트라이 캐치문 이후에 무조건 동작하기 때문에 주로 리소스 해제,클린업을 위한 코드를 작성한다.

## 배열

#### New Array()

1. 단일 숫자를 넣으면 해당 넓이를 가진 빈 배열을 만든다.
   > New Array(5)

#### Array.of()

1. 대괄호([])로 배열을 만드는 방법보다 성능적으로 떨어지고 장점이 없어 사용하지않는다

#### Array.from()

1. 유사배열이나 이터러블 객체를 배열로 변환해준다.

#### shift()

1. 요소를 하나씩 왼쪽으로 이동
   > 배열 전체를 이동시키기때문에 push나 pop보다 성능적으로 느리다

#### unshift()

1. 요소를 하나씩 오른쪽으로 이동
2. 새로운 요소를 배열의 맨앞쪽에 추가하고, 길이를 반환
   > 배열 전체를 이동시키기때문에 push나 pop보다 성능적으로 느리다

#### slice()

1. begin부터 end(미포함)까지 얕은 복사본을 새로운 배열 객체로 변환
2. 원본 배열은 바뀌지 않는다.

#### concat()

1. 두 개 이상의 배열을 병합하여 새로운 배열을 반환
2. 원본 배열은 바뀌지 않는다

#### find()

1. 배열에서 만족하는 첫번째 요소를 반환

#### map()

1. 함수를 호출한 결과를 모아 새로운 배열을 반환

#### sort()

1. 배열을 정렬하고 정렬한 배열을 반환

#### filter()

1. 주어진 조건에 적합한 얕은 복사본 배열을 반환

#### reduce()

1. 리듀서 함수의 반환 값은 누산기에 할당되고, 누산기는 순회 중 유지되므로 결국 최종 결과는 하나의 값
2. 네개의 인자를 가진다 - 누산기(acc), 현재 값(cur), 현재 인덱스(idx), 원본 배열(src)

## 객체

1. 객체에서 점표기법으로 표현할 수 없는 값은 대괄호 표기법을 사용한다

```
  person = {last name: y, 1: 1, first name: my }
  person.last name - x
  person.first name - x
  person.1 -x
  person["last name"] - o
  person["first name"] - o
  person[1] - o
```

2. key와 value 이름이 같을 경우 생략 가능하다

```
  {
    name: name,
    age: age
  }
  {
    name,
    age
  }
```

3. 객체 구조 분해

```
const o = { p: 42, q: true };
const { p: foo, q: bar } = o;

console.log(foo); // 42
console.log(bar); // true
```

## ✅ 프로토타입(Prototype)

1. 모든 객체는 prototype에 대한 정보를 갖고있다.
2. 생성자에서 접근할때는 prototype, 객체에서 접근할때는 **proto**
3. [[Prototype]]은 사실 접근이 불가능한 객체라 접근을 하기위해 **proto**를 사용한다.

✅ Prototype에 대한 이해가 부족해 다시 한번 학습이 필요

## 이벤트 리스너

1. 이벤트를 등록하는 방법은 3가지가있다.
1. html코드에 직접 삽입 하는방법

```
  <button onclick="clickEvent"/>
```

2. js코드에 직접 이벤트를 적는 방법

```
  document.querySelector("button").onclick = clickEvent;
```

3. addEventListener를 사용하는 방법

```
  document.querySelector("button").addEventListener("click", cliekEvent);
```

- 1번은 HTML코드와 JS코드가 같이있어 유지보수에도 좋지못하고 혼란을가져온다.
- 2번은 이벤트를 한번에 한개만 추가가능하여 권장하지 않는다.
- 3번은 이벤트도 여러개 추가 가능하고 제거도 가능하여 권장한다.

#### 버블링

1. 이벤트가 상위 요소로 전파되는 단계
2. 버블링을 중단하기 위해서는 stopProggation()을 사용해야한다.
   > 꼭 필요한 경우를 제외하고는 버블링을 중단해서는 안된다. why? stopProggation으로 버블링을 막은 영역은 분석이 제대로 되지 않기 때문입니다.

#### 캡처링

1. 이벤트가 하위 요소로 전파되는 단계

## Script

1. 스크립트 파일을 동적으로 추가가 가능하다.
   > 하지만 노출이 쉽게되기때문에 신중하게 사용해야한다.

## 고급함수

#### 순수 함수

1. 입력값이 있고 항상 같은 값을 내는 함수이다.

#### 부수 효과(Side Effect)

1. 함수 내에서 어떤 구현이 함수 외부에 어떤 영향을 끼치는 경우 해당 함수는 Side Effect가 있다고 말한다.

- 순수함수와 비순수함수(Side Effect가 포함된)는 함수명에서 유추 가능하도록 하면 좋다.

#### 팩토리 함수

1. 함수가 객체를 반환할때, 이 함수를 공장 함수 혹은 팩토리 함수라 부른다.

#### 클로저

1. 클로저는 주변 상태에 대한 참조와 함께 묶인 함수의 조합, 즉 클로저는 내부함수에서 외부함수의 범위에 대한 접근을 제공한다.
   > 예제 1과 예제 2는 같은 결과를 만들어낸다.

- 예제 1

```
function init() {
  var name = "my"; // name은 init에 의해 생성된 지역 변수이다.
  function displayName() {
    // displayName() 은 내부 함수이며, 클로저다.
    console.log(name); // 부모 함수에서 선언된 변수를 사용한다.
  }
  displayName();
}
init();
```

- 예제 2

```
function makeFunc() {
  const name = "Mozilla";
  function displayName() {
    console.log(name);
  }
  return displayName;
}

const myFunc = makeFunc();
myFunc();
```