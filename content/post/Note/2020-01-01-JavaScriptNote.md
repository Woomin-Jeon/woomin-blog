---
title: "Note - JavaScript"
date: 2020-01-01
tag: ["Note"]
---

#### includes 메서드  

  배열에 특정 요소가 있는지 판별한 후 True/False를 반환한다.

  ```javascript
  const arr = [1, 2, 3, 4, "incl"];  
  arr.includes(3) -> True  
  arr.includes("incl") -> True  
  ```
  
<br />

#### split 메서드  

  String 객체를 지정한 구분자를 이용하여 여러 개의 문자열로 나눈다.
  
  ```javascript
  const arr = "I love programming";  
  arr.split(' ') -> ["I", "love", "programming"]  
  ```

  <br />

#### join 메서드  

  배열의 모든 요소들을 지정한 구분자를 이용하여 하나의 문자열로 만든다.
  
  ```javascript
  ex) const arr = ["I", "love", "programming"];  
  arr.join('') -> "I,love,programming"  
  arr.join(' ') -> "I love programming"  
  arr.join('-') -> "I-love-programming"  
  ```
  
<br />

#### sort 메서드  

  배열의 요소를 적절하게 정렬한 후 배열을 반환하는 것이지만 여기서는 오름차순으로 배열하는 법과 내림차순으로 배열하는 법을 설명한다. 
  
  ```javascript
  ex) const arr = [2, 4, 1, -5, 3];  
  arr.sort((a, b) => a - b) -> [-5, 1, 2, 3, 4]  
  arr.sort((b, a) => b - a) -> [4, 3, 2, 1, -5]  
  cf) "a - b > 0" 이면 배열에서 a, b의 자리를 바꾸는 메서드라고 보면 된다.  
  ```  

  cf) 참고로 문자 character도 대소 비교가 가능하다.  
  예를 들어, `a < b < c < d < ... < y < z` 이다.

#### sort 메서드에 대한 조금 더 깊은 이해

- 배열 arr = [2, 3, 1, 5, 4] 가 있다고 가정하자.
- arr.sort((a, b) => a - b)는 배열 arr을 오름차순 [1, 2, 3, 4, 5]로 만든다.
- 이 과정을 깊게 살펴보면, 먼저 sort가 처음 돌때, (a, b)는 (2, 3)을 의미한다. a=2, b=3. 그리고 함수의 내용이 1보다 크면 (a, b)를 (b,a로 바꿔주는 역할을 하는 것이 sort이다.
- 즉, 2 - 3 = -1로 1보다 작기때문에 (a, b)의 위치는 바뀌지 않는다.
- 다음으로 sort가 돌면, 다시 처음부터 (2, 3)에 대해 판단을 하고 위의 경우에서 보았듯이 자리는 그대로 놥둔다. 이제 (a, b)는 (3, 1이된다. 3 - 1은 2이므로 1보다 크기 때문에 (a, b)의 위치는 (b, a)로 바뀌어서 이 시점에서의 arr은 [2, 1, 3, 5, 4]가 된다.
- 이제 다시 또 다음으로 sort가 돌면, 처음의 (2, 1)에 대해 이 두 수는 1보다 큰 값을 반환하므로 자리가 바뀌고 [1, 2, 3, 5, 4]가 된다.
- 이제 다시 또 다음으로 sort가 돌면, 배열 arr의 앞의 [1, 2, 3] 은 위의 경우처럼 넘어가고 (3, 5)에 대한 판단을 한다.
- 이런식으로 sort는 계속 배열 arr을 돌면서 원소들을 정렬한다.
- 그러므로, arr.sort((a, b) => "함수의 내용") 으로 함수의 내용을 우리가 만들고 그 반환값을 1, -1, 0 으로 정해줌으로써 조건에따른sort를 가능하게 한다. 아래는 이에대한 예시이다.

    ```javascript
    failureRate = failureRate.map((v, i) => v = { rate: v, index: i+1 });
    failureRate.sort((a, b) => {
      return a.rate > b.rate ? -1 :
      a.rate < b.rate ? 1 :
      a.rate == b.rate ?
        a.index < b.index ? -1 :
        a.index > b.index ? 1 : 0 :
      0;
    });
    ```

<br />

#### trim 메서드  

  문자열 양 쪽 끝의 공백을 제거해주는 메서드이다.
  
  ```javascript
  ex) const arr = "　　　Hello　　　";  
  arr.trim() -> "Hello"
  ```

<br />

#### 몫 구하기  

  JavaScript에서 몫을 구하기 위해서는 그냥 a/b 하면 안되고, parseInt()를 사용해야 한다.  
  예를들면, 12 / 5 = 2.4 가 나오지만 parseInt(12 / 5, 10)으로 하면 2가 나오게 된다.  
  참고로 위의 예시 parseInt(x / y, d)에서 d = 10은 10진수를 의미한다.

<br />

#### 숫자 합치기  

  JavaScript에서 여러 숫자를 하나로 합치는 방법은, 10 + ‘’ + 5 = “105” 이것과 같이 하면 된다.  
  그리고 이걸 다시 숫자로 바꾸려면, +(10 + ‘’ + 5) = 105 로 하면 된다.

<br />

#### 객체를 담은 배열에서 객체의 프로퍼티를 조건에 맞게 변경하는 방법  

  객체를 담은 배열 arr = [{...}, {...}, ... ]에서, arr 의 객체 프로퍼티를 변경하는 방법은 .map 메서드와 삼항연산자를 이용하여 조건을 부여한 후 바꾸면 된다.  
  
  ```javascript
  arr: arr.map((v) => (v.property == condition ? v : { …v, prop: v.prop + 1 }))
  ```

<br />

#### 함수에서 발생하는 에러를 해결하기 위한 5가지 step  

  1. 함수 안에 들어가는 x 값에 문제는 없는가
  2. 함수에 x 값이 제대로 잘 들어갔는가
  3. 함수 안에서 x 값이 잘 처리되고 있는가
  4. 함수를 통해 처리된 x 값의 결과물 y가 함수 바깥으로 나오는 과정에 문제는 없는가
  5. 결과물 y가 제대로 잘 return 되었는가

<br />

#### 배열에서 조건에 맞는 원소가 몇개인지 확인하는 방법  
  
  ```javascript
  arr.filter((v) => 조건식).length;
  ```

<br />

#### 배열을 객체로 만드는 방법  

  배열 result=[…]에 대해서
  
  ```javascript
  result = result.map(v, i) => ({ index: i, value: v });
  ```

  cf) 위의 예시 .map((v, i))에서 map의 두번째 인자 i는 index를 의미한다. 위와 같이 설정하면 자동으로 index값을 0 부터 넣어준다.

<br />
  
#### ESLint 사용하는 법

- VSCode에서 ESLint 확장 프로그램을 설치한다.
- $ npm i eslint
- $ npx eslint --init
- eslintrc.js에서 rules에 .js, .jsx 확장자 무시하도록 설정한다.  
  -> "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],

<br />

#### JavaScript 올림, 내림, 반올림 메서드

- Math.floor() 메서드  
  소숫점 아래 부분을 내림하여 정수만 남기는 메서드이다.
  
  ```javascript
  Math.floor(5.64) -> 5
  Math.floor(3.99) -> 3
  Math.floor(-5.33) -> -6
  ```

- Math.round() 메서드  
  소숫점 아래 부분을 반올림하여 정수만 남기는 메서드이다.

  ```javascript
  Math.round(5.95) -> 6
  Math.round(5.5) -> 6
  Math.round(5.45) -> 5
  Math.round(-5.75) -> -6
  Math.round(-5.05) -> -5
  ```

- Math.ceil() 메서드  
  소숫점 아래 부분을 올림하여 정수만 남기는 메서드이다.
  
  ```javascript
  Math.ceil(0.95) -> 1
  Math.ceil(7.01) -> 8
  Math.ceil(-5.95) -> 5
  Math.ceil(-9.01) -> 9
  ```

<br />

#### JavaScript 객체 프로퍼티 추출과 관련된 메서드  
  
  ```javascript
  const example = {
    id: 'woomin',
    sex: 'male',
    contents: 'what'
  }

  Object.entries(example)  
    -> "id: woomin", "sex: male", "contents: what"
  Object.keys(example)
    -> ["id", "sex", "contents"]
  Object.values(example)
    -> ["woomin", "male", "what"]
  ```

<br />

#### Math.sqrt 메서드  

  제곱근을 반환해주는 메서드이다.

  ```javascript
  Math.sqrt(121) -> 11
  Math.sqrt(9) -> 3
  Math.sqrt(122) -> 11.045361
  ```

<br />

#### substr 메서드  

  String.substr(a, b) 문자열 추출 메서드. 인덱스 a에서부터 b개 만큼 잘라서 반환.

  ```javascript
  const arr = [1, 2, 3, 4, 5];
  arr.substr(1,3) -> [2, 3, 4]
  ```

<br />

#### slice와 splice 메서드  

  지금까지 slice와 splice의 차이는 원본 배열을 건드리냐 아니냐의 차인줄 알고 slice를 splice 처럼 쓰려고 했으나 들어가는 인자값이 다르다는 것을 알게되었다.  
  먼저, Array.splice(n, m)은 원본배열 Array를 변형시키며, n번째 인덱스에서부터 m개 만큼 제거한다.  
  Array.slice(n, m)은 원본배열 Array를 변형시키지 않으며, n번째 인덱스에서부터 m번째 인덱스 `전까지` 제거하여 반환한다.  
  쉽게 예시를 보자,

  ```javascript
  const arrSplice = ['A', 'B', 'C', 'D', 'E'];
  const arrSlice = ['A', 'B', 'C', 'D', 'E'];

  const forSplice = arrSplice.splice(1, 3);
  const forSlice = arrSlice.slice(1, 3);

  console.log(forSplice) -> ['B', 'C', 'D']
  console.log(arrSplice) -> ['A', 'E']
  
  // arrSlice[1]에서부터 arr.slice[3]전까지 -> B ~ C까지(D 전까지)
  console.log(forSlice) -> ['B', 'C']
  console.log(arrSlice) -> ['A', 'B', 'C', 'D', 'E']
  ```

<br />

#### 삼항연산자와 "&&"  
  
  ```javascript
  const a = 1;
  const b = 2;
  const answer = [];

  // 만약 a가 b보다 작은 경우 answer배열에 그 값을 넣고 싶다면,
  a < b ? answer.push(a) : ''; // 참일 경우 a값을 삽입, 아닐경우 아무 값 반환.
  // 하지만 이렇게 하는 것보다 논리연산자 "&&"을 사용하는 것이 더 명시적이다.
  a < b && answer.push(a);
  ```

<br />
  
#### 10진수 x를 y진수로 바꾸는 법 : x.toString(y)  

  예를 들어, 10진수 5를 3진수로 바꾸려면,

  ```javascript
  const value = 5;
  const changedNum = value.toString(3)
  console.log(changedNum) -> "12"
  ```

<br />

#### x진수로 쓰여진 value가 10진수로 얼마인지 판단하는 법 : parseInt(value, x)  

  예를 들어 2진수로 쓰여진 1010을 10진수로 보려면,

  ```javascript
  const value = 1010;
  const changedNum = parseInt(value, 2);
  console.log(changedNum) -> 10
  ```

<br />

#### 문자를 아스키코드로, 아스키코드를 문자로 변환하는 메서드  
  
  ```javascript
  const a = "a";
  
  // character → ASCII
  a.charCodeAt(0) -> 97

  // ASCII → character
  String.fromCharCode(97) -> "a"
  ```

<br />

#### 자릿수를 맞춰주는 메서드 : padStart()

```javascript
const num = '1';
num.padStart(3, '0') -> '001'
num.padStart(4, '*') -> '***1'
```

<br />

#### Map 객체

```javascript
const map = new Map();
const id = 'userID';
let name;

name = 'apple';
map.set(id, name); -> userID: 'apple'

name = 'banana';
map.set(id, name); -> userID: 'banana;

map.get(id) -> 'banana'
```

<br />

#### 배열에서 가장 큰 값을 찾는 법

  ```javascript
  const arr = [1, 2, 3, 4, 5];
  Math.max(...arr) -> 5
  ```

<br />

#### 부분 집합인지를 판별하는 법

  ```javascript
  const arr = [1, 2, 3, 4, 5, 6];
  const subArr = [1, 3, 4];

  /* subArr이 arr의 부분집합인지를 확인하는 방법으로
     그동안에는 every와 includes를 이용했었다. */
  subArr.every(v => arr.includes(v));
  
  /* 하지만 이렇게되면 subArr를 순회하며(every), arr도 순회하기 때문에(includes)
     복잡도가 O(n^2)이 나온다. 그렇기 때문에 효율 좋은 방법을 생각해보았다.
     그리고 includes라는 메서드가 문자열에서 해당 문자열이 포함하는 지를 살펴보는
     것이라는 걸 이용하여, 다음과 같이 부분집합인지를 구한다. */
  arr.toString().includes(subArr.toString());
  ```

<br />