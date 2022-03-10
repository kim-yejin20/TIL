## 목차

[0. 함수와 메소드 차이](#0-함수와-메소드-차이)  
[1. concat() : 배열 합치기](#1-concat)  
[2. push(), unshift() : 배열에 항목 추가](#2-push-unshift)  
[3. pop(), shift() : 배열에 항목 제거](#3-pop-shift)  
[4. reduce() : ](#4-reduce)

<br>
<hr>
<br>

## 0. 함수와 메소드 차이

- function : 기능을 수행.
- method : 함수처럼 기능을 수행.
- <strong>function과 method 차이점</strong> : method는 클래스 및 객체(object)와 연관되어있는 함수. 클래스 내에 선언되어 있는 함수가 method. 클래스 및 객체와 연관되어있는 것이라면 "method"이고, 그것들과 상관없이 독립적으로 존재하는 것이 "function".

- 함수(function)은 sum(), abs() 처럼 독립적으로 사용.
- 메소드(method)는 a라는 객체가 존재할 때 a.upper(), a.concat() 같은 형태로 사용.

<br>
<br>

## 1. concat()

배열을 합친다.

<br>

`array.concat([value[, value2[, ... [,valueN]]]])`

- 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환.
- 기존 배열이나 값을 변경시키지 않음.

```javascript
const arr1 = [1, 2, 3, 4];
const arr2 = [5, 6, 7];
const arr3 = [8, 9];

console.log(arr1.concat(arr2));
// ->  [ 1, 2, 3, 4, 5, 6, 7 ]

console.log(arr1.concat(arr2, arr3));
// -> [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
```

<br>
<br>

## 2. push(), unshift()

`push()` : 배열 "끝"에 항목을 추가한다.  
`unshift()` : 배열 "앞"에 항목을 추가한다.

- 호출한 배열의 새로운 length 속성을 반환.
- 기존 배열을 변경시킴.

```javascript
const arr = [1, 2, 3, 4, 5];

console.log(arr.push('끝')); // 6
console.log(arr); // [ 1, 2, 3, 4, 5, '끝' ]

console.log(arr.unshift('앞')); // 7
console.log(arr); // [ '앞', 1, 2, 3, 4, 5, '끝' ]
```

<br>
<br>

## 3. pop(), shift()

`pop()` : 배열 "끝"에 항목을 제거한다.  
`shift()` : 배열 "앞"에 항목을 제거한다.

- 제거한 항목을 반환.
- 기존 배열을 변경시킴.

```javascript
const arr = [1, 2, 3, 4];

console.log(arr.pop()); // 4
console.log(arr); // [ 1, 2, 3 ]

console.log(arr.shift()); // 1
console.log(arr); // [ 2, 3 ]
```

<br>
<br>

## 4. reduce()

배열의 각 요소에 대해 reducer 함수를 실행

`arr.reduce(callback[, initialValue])`

- 누적 계산의 결과 값을 반환.

```javascript
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10
```

! 참고: initialValue를 제공하지 않으면, reduce()는 인덱스 1부터 시작해 콜백 함수를 실행하고 첫 번째 인덱스는 건너 뛴다. initialValue를 제공하면 인덱스 0에서 시작한다.

<br>

#### (1) 배열의 모든 값 합산하기

```javascript
const sum = [0, 1, 2, 3];
sum.reduce(function (a, b) {
  return a + b;
}, 0);

// output: 6
```

화살표 함수로도 작성이 가능.

```javascript
const sum = [0, 1, 2, 3];
sum.reduce((a, b) => a + b, 0);

// output: 6
```

<br>

#### (2) 객체 배열에서의 값 합산

: 객체로 이루어진 배열에 들어있는 값을 합산하기 위해서는 반드시 초기값(initialValue)을 주어 각 항목이 함수를 거치도록 해야한다. 화살표 함수로도 작성 가능.

```javascript
const initialValue = 0;
const sum = [{ x: 1 }, { x: 2 }, { x: 3 }];
sum.reduce(function (a, b) {
  return a + b.x;
}, initialValue);

// output: 6
```

<br>

#### (3) 객체 내의 값 인스턴스 개수 세기

```javascript
const arr = ['Python', 'Javascript', 'C', 'Javascript', 'Java'];
const count = arr.reduce(function (a, b) {
  if (b in a) {
    a[b]++;
  } else {
    a[b] = 1;
  }
  return a;
}, {});

console.log(count);
// -> { Python: 1, Javascript: 2, C: 1, Java: 1 }
```


