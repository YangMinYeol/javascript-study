## 타입
1. undefined는 정의되지 않은걸 뜻하므로 undefined로 정의하는일은 없어야 한다.
2. 배열과 객체는 동등연산자(==)와 일치연산자(===)로 비교해도 false가 나온다.
3. Falsy와 Truthy란 false와 true에 역할을 하는 값
    1. Falsy: 0, Nan, false, null, undefined, "" 
    2. Falsy 이외에는 모두 true
4. 대문자 상수란 기억하기 힘든값을 별칭으로 빼서 사용할 경우 사용 
    1. 값보다 상수를 이용하는것이 오타를 낼 확률이 낮다. 값보다 상수가 훨씬 유의미하다.
    2. 코드 가독성이 좋아진다.