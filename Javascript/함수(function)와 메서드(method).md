## 목차

[0. 함수와 메소드 차이](#0-함수와-메소드-차이)  
[1. concat() : 배열 합치기](#1-concat)  
[2. push(), unshift() : 배열에 항목 추가](#2-push-unshift)  
[3. pop(), shift() : 배열에 항목 제거](#3-pop-shift)  
[4. reduce() : ](#4-reduce)  
[5. substr(), substring(), slice() : 문자열 자르기 ](#5-substr-substring-slice)

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

배열의 각 요소에 대해 reducer 함수를 실행한다.

<br>
<h3>구문</h3>

`arr.reduce(callback[, initialValue])`

<br>

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

## 5. substr(), substring(), slice()

<br>

<h3> (1) substr() </h3>

`substr()` : 문자열에서 특정 위치에서 시작하여 특정 문자 수 만큼의 문자를 반환

<br>
<h3>구문</h3>

`str.substr(start[, length])`

<br>
<h3>매개변수</h3>

- `start` : 추출하려는 문자의 시작 위치. 음수일 경우 `문자열총길이 + start` 값으로 취급.
- `length` : 옵션값, 추출할 문자들의 총 숫자. 0 혹은 음수이면, 빈 문자열을 반환한다. 생략되면 문자열의 끝까지 추출하여 반환한다.

```javascript
const string = '일이삼사오육칠팔구십';

console.log(string.substr(1, 2)); // '이삼'
console.log(string.substr(-4, 2)); // '칠팔'
console.log(string.substr(-1)); // '십'
console.log(string.substr(-4)); // '칠팔구십'
console.log(string.substr(-20, 3)); // '일이삼'
console.log(string.substr(20, 3)); // ''
```

<br>

<h3> (2) substring() </h3>

`substring()` : 문자열 객체의 시작 인덱스로부터 종료 인덱스 전까지 문자열의 부분 문자열을 반환한다.

<br>
<h3>구문</h3>

`str.substring(indexStart[, indexEnd])`

<br>
<h3>매개변수</h3>

- `indexStart` : 반환문자열의 시작 인덱스
- `indexEnd` : 옵션. 반환 문자열의 마지막 인덱스(포함하지 않음)

<br>
<h3>반환값</h3>
기존 문자열의 부분 문자열을 반환

<br>
<br>
<h3> 설명 예시 </h3>

- `indexEnd` 가 생략된 경우, substring() 문자열의 끝까지 모든 문자를 추출

```javascript
const anyString = 'AaBbCcDdEe';

console.log(anyString.substring(4)); // 'CcDdEe'
```

<br>

- `indexStart` 가 `indexEnd` 와 같을 경우, substring() 빈 문자열을 반환

```javascript
const anyString = 'AaBbCcDdEe';

console.log(anyString.substring(3, 3)); // ''
console.log(anyString.substring(4, 4)); // ''
```

<br>

- `indexStart` 가 `indexEnd` 보다 큰 경우, substring() 은 두 개의 인자 순서를 바꾼 것처럼 작동

```javascript
const anyString = 'AaBbCcDdEe';

console.log(anyString.substring(0, 1)); // 'A'
console.log(anyString.substring(1, 0)); // 'A'
```

<br>

- 0보다 작은 인자값을 가지는 경우에는 0으로 , string.length보다 큰 인자값을 가지는 경우에는 string.length로 처리.

```javascript
const anyString = 'AaBbCcDdEe';
console.log(anyString.length); // 10

console.log(anyString.substring(-1, 10)); // 'AaBbCcDdEe'
console.log(anyString.substring(0, 10)); // 'AaBbCcDdEe'
console.log(anyString.substring(0, 17)); // 'AaBbCcDdEe'
```

<br>
<br>
<h3> (3) slice() </h3>

`slice()` : 문자열의 일부를 추출하면서 `새로운 문자열`을 반환

<br>
<h3>구문</h3>

`str.slice(beginIndex[, endIndex])`

<br>
<h3>매개변수</h3>

- `beginIndex` : 0부터 시작하는 추출 시작점 인덱스. 음수일 경우, `strLength(문자열 길이) + beginIndex`로 취급. `strLength `보다 크거나 같은 경우, slice()는 빈 문자열을 반환.

- `endIndexOptional` : 0부터 시작하는 추출 종료점 인덱스로 `그 직전까지 추출`(인덱스 위치의 문자는 추출에 포함되지 않음!). 생략시, silce()는 문자열 마지막까지 추출. 음수라면, `strLength(문자열 길이) + endIndex` 로 취급.

<br>
<h3>반환 값</h3>
문자열의 추출된 부분을 담는 새로운 문자열이 반환

<br>
<br>
<h3>설명 예시</h3>

- slice()는 endIndex를 포함하지 않고 추출한다. str.slice(1, 4)는 두 번째 문자부터 네 번째 문자까지 추출.

```javascript
const str = '1234 567 890';

console.log(str.slice(1, 4)); // '234'
console.log(str.slice(1, 5)); // '234 '  -> 띄어쓰기 포함해서 추출
```

<br>

- str.slice(2, -1)는 세 번째 문자부터 문자열의 마지막에서 두 번째 문자까지 추출.

```javascript
const str = '1234 567 890';

console.log(str.slice(2, -1)); // '34 567 89'
```

<br>

- slice()로 새 문자열 생성

```javascript
const str = '1234 567 890';
const str1 = str.slice(1, 4);
const str2 = str.slice(7);
const str3 = str.slice(-4);

console.log(str1); // '234'
console.log(str2); // '7 890'
console.log(str3); // ' 890'
```

<br>
<h3> (4) 각각 차이점 </h3>

- `substring()` 와 `substr()` 차이점  
  `substring()`의 인수는 시작 및 끝 인덱스를 나타냄
  `substr()`의 인수는 시작 인덱스와 반환된 문자열에 포함할 문자의 수를 나타냄

```javascript
const test = 'AbcDefgH';

console.log(test.substring(2, 5)); // 'cDe'
console.log(test.substr(2, 5)); // 'cDefg'
console.log(test.substr(2, 3)); // 'cDe'
```

<br>

- `substring()` 와 `slice()` 차이점  
  시작인덱스가 끝 인덱스보다 클 경우, `substring()`는 두 인수를 교환해서 반환하고 `slice()`는 빈 문자열을 반환  
  인수 중 하나 이상 음수인 경우, `substring()`는 인수를 있는 것처럼 처리하고 `slice()`는 Nan은 0으로 취급, 음수는 문자열 끝에서 역방향으로 계산

```javascript
const test = 'AbcDefgH';

// 동일한 값 출력
console.log(test.substring(2, 5)); // 'cDe'
console.log(test.slice(2, 5)); // 'cDe'

// 부정적인 인수 : 시작 인덱스 > 끝 인덱스 == 반환값 다름
console.log(test.substring(5, 2)); // 'cDe'
console.log(test.slice(5, 2)); // ''

// 부정적인 인수 : 음수 인덱스
console.log(test.substring(-5, 2)); // 'Ab'
console.log(test.substring(-5, -2)); // ''

console.log(test.slice(-5, 2)); // ''
console.log(test.slice(-5, -2)); // 'Def'
```
