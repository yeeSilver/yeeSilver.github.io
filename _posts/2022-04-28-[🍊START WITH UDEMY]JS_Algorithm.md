# [🍊START WITH UDEMY] JS 알고리즘 & 자료구조 마스터클래스 뽀개기 - 1일차
2022 START WITH UDEMY 챌린저로 선발이 돼서, 마침 공부하고 싶었던 JS 알고리즘 공부를 지원 받아 할 수 있게 되었어요!

[글로벌 Best] JavaScipt 알고리즘 & 자료구조 마스터클래스 수업을 수강해보도록 하겠습니다. 

[👉JavaScipt 알고리즘 & 자료구조 마스터클래스 수업 바로가기](https://www.udemy.com/course/best-javascript-data-structures/)
![image](https://user-images.githubusercontent.com/48678872/165695063-75748d27-8772-443b-9f6e-4c2258d1fef3.png)
유데미에서 할인을 하고 있으니 착한 가격에 들어보시는 것도 추천합니다.

수업은 영어권 강사님이 진행하시지만 한글 자막이 지원되기 때문에 큰 걱정 없이 잘 들을 수 있습니다. 

그럼, 시작해보도록 하겠습니다.

# 시간 복잡도

## [0] 들어가기 전에, 왜 빅오 표기를 배워야 하는가?

하나의 결과를 도출하기 위해서 딱 하나의 코드만 정답이 있는 건 아니다. 수 만가지의 방법이 있을 수 있다. 

그렇다면 어떤 것이 더 효율적인 방법일까?

여기서 빅오(Big O)가 등장한다. 

> 빅오란 여러가지 코드를 일반적으로 서로 비교하고 성능을 평가하는 방법이다.
> 

## Big O

알고리즘 성능을 분석하기 위해서 빅오 표기를 사용한다. 빅오를 통해서 시간 복잡도와 공간 복잡도를 표현할 수 있다. 빅오로 측정되는 알고리즘의 시간과 공간 복잡도는 하드웨어의 영향을 받지 않고 오로지 알고리즘 작동에 관하여만 측정한다.

## [1] 코드 시간 재기 : performance.now()

`performance.now()` 는 브라우저가 문서를 만드는 시간, 창이 열린 시간을 알려준다.

```jsx
function 함수{
//함수내용
}

const beforeFunc = performance.now();
함수();
const afterFunc = performance.now();
console.log(`시간경과 : ${(afterFunc - beforeFunc) / 1000} seconds.`)
```

1000분의 1초 단위로 되어있기 때문에 1000으로 나눠주어야 한다. 

→ 함수 실행하는 데 드는 시간이 일정하게 출력되진 않는다. 기기에 따라, 동시에 실행하고 있는 프로그램 등에 따라 함수가 동작하는 시간은 달라진다. 

🍋 코드 작동 시간을 출력하여 비교하는 것 보다, 빅오 표기법을 이용하여 비교하면 훨씬 간단하고 간편히 할 수 있다. 

## [2]빅오 표기 공식 소개

### 1. O(n) : n이 증가할 수록 커지는 연산 횟수

```jsx
 for (let i = 0; i < n; i++) {
    console.log(i);
  }
//O(n)
```

n이 커질수록 루프 안의 연산을 실행하는 횟수가 늘어나기 때문에 O(n)이다. 즉 n만큼의 연산이 일어나기 때문에 O(n)이라고 할 수 있다. 

```jsx
  for (let j = n - 1; j >= 0; j--) {
    console.log(j);
//O(n)
```

위의 코드 또한 n만큼의 연산이 일어나는 것이기 때문에 O(n)이다.

```jsx
function count(n) {
  console.log("올라간다");
  for (let i = 0; i < n; i++) {
    console.log(i);
  }
  console.log("내려간다");
  for (let j = n - 1; j >= n; j--) {
    console.log(j);
  }
}
//O(2n) = O(n)
```

따라서 위의 코드는 O(n)과 O(n)의 조합이다.
아! 그렇다면 O(2n)이겠구나! 라고 생각할 수도 있지만 틀렸다.

 
빅오 표기에서는 상수는 무시하기 때문에 2n은 n으로 간주한다. 따라서 O(n)이 4개 있든 5개 있든 O(n)이 된다. 

### 2. O(n^2)

```jsx
function print(n){
	for(const i = 0; i < n; i++){
		for(const j = 0; j < n; j++){
				console.log(i,j);
			}
	}
}
```

이번 코드는 위와 다르게 `중첩`이 되어있다. 
즉,  n번씩 실행하는 코드안에 또 n번씩 실행하는 코드가 있다는 것이다. 이렇게 O(n) 연산 안에 O(n)연산이 중첩되어 있으면  `O(n^2) n의 제곱`이 된다.

![지워 PNG](https://user-images.githubusercontent.com/48678872/165691920-93ee6dae-00eb-44c7-b6b5-167dde4c7bff.png)

 n이 커질수록 실행 시간이 n 제곱 값으로 늘어난다. 

## [3]빅오 표현식 단순화 하기

### 1. 상수항 무시

상수는 무시하여 최대한 단순하게 표현한다.

```jsx
O(100) => O(1)
O(2n) => O(n)
O(10n^2) => O(n^2)
```

### 2. 최고차항만 표시

최고차항만 남긴다.

```jsx
O(5n + 10) => O(n)
O(n^2 + 2n + 5) => O(n^2)
```

## 예시를 보자 : O(n)과 O(1)의 차이

1. O(n)
    
    ```jsx
    function up(n){
    	for (const i = 1; i <= Math.max(3, n); i++){
    		console.log(i)
    	}
    }
    // O(n)
    ```
    

> **Math.max()**
> 

`Math.max(입력값1, 입력값2 .... )` 입력 받은 값들 중에서 가장 큰 수를 반환한다. 

위의 코드에서 n이 1000만이 들어간다면 루프는 100만번 실행될 것이다. 즉, n이 커질수록 함수 실행 숫자도 증가한다는 것..! 

따라서 함수 실행 즉, 연산의 개수가 n의 영향을 받기 때문에 `O(n)`라고 할 수 있다. 

1. O(1)
    
    ```jsx
    function up(n){
    	for (const i = 1; i <= Math.min(3, n); i++){
    		console.log(i)
    	}
    }
    // O(1)
    ```
    
    Math.min(입력값1, 입력값2 ... ) 은 입력 받은 값들 중에서 가장 작은 숫자를 반환한다.
    
    위의 코드에서 `Math.min(3, n)` 은 3과 n중 작은 수를 반환하는 코드이다. n이 100만번이 되든, 그 이상이 되든, 3보다 커지면 3번만 실행될 것이다. 즉, n의 증가는 함수 실행에 아무 영향도 주지 않게 된다. 
    
    위의 코드에서 루프 횟수에 영향을 주는 것은 3 즉, 상수가 된다. 
    

지금 까지 입력이 커질 수록 알고리즘의 실행 횟수가 얼만큼 늘어나는지 속도가 어떻게 바뀌는 지 (time complexity) 시간 복잡도에 대해 알아보았다. 이제는 공간 복잡도 (Space complexity)에 대해 알아보도록 하자. 

# 공간 복잡도 Space complexity

입력이 커질수록 알고리즘이 얼마나 많은 공간을 차지하는 지에 대해 알아보도록 하자.

물론 입력값이 커지면 당연히 복잡도도 증가하겠지만 여기서는 입력 값은 무시하고 알고리즘 자체가 어떤 영향을 주는 지에 대해 알아보도독 하겠다. 

### 1) 원시타입( booleans, numbers, undefined, null)은 JS에서 모두 고정 공간 O(1)이다.

> Most primitives( booleans, numbers, undefined, null) are **constant space**
-udemy[글로벌best] JS 알고리즘& 자료구조 마스터크래스



### 🍋여기서 잠깐! constant space가 무엇일까?

고정 공간(constant space)이란 입력 값, 알고리즘 실행과는 관련 없이 사용되는 공간이다. 변수를 저장하는 등의 공간이라고 생각하면 된다. 

booleans, numbers, undefined, null은 상수 공간으로 취급된다는 것이다. 
따라서 입력의 크기와는 상관 없이 입력값이 1이든 100이든 고정적인 공간을 갖는다. 

고정 공간은 c(상수)라고 할 수 있으며 O(1)이다.

### 2. 문자열은 O(n)공간을 갖는다.

쉽게 생각하면, 50자가 100자보다는 공간을 덜 차지할 것이다. 
즉, 입력 값에 따라서 공간을 차지하는 정도가 변하기 때문에 O(n)인 것이다. 

### 3. reference타입 (객체, 배열 등)은 대부분 O(n)이다.

여기서 n은 배열의 길이 혹은 객체의 키 개수일 수 있다. 
길이가 10인 배열보다 100인 배열이 더 많은 공간을 차지하기 때문에 배열의 길이인 n이 커질수록 차지하는 공간도 커진다. 

## 예시를 보자

```jsx
function add(arr){
	const newArr = [];
	for( let i =p; i < arr.length; i++){
		newArr.push(i + arr[i]);
	}
	return newArr;
}
//O(n) space
```

`const newArr = [];` 은 알고리즘의 횟수와 관계없이 변수 선언으로 할당되는 부분이다. 이는 c 즉 O(1)의 공간 복잡도를 가진다고 할 수 있다. 

`newArr`은 위의 고정 공간과 다르다. 
arr 값이 커질수록 push되는 원소의 양이 많아진다. 따라서 `newArr`가 차지하는 공간은 arr에 비례하게 커지기 때문에 O(n) 공간을 차지한다.

위의 코드의 공간 복잡도는 O(n) + c 이지만 최고차항만 남기기 때문에 O(n)으로 단순화 할 수 있다. 

### 퀴즈 타임

```jsx
아래 함수에 대한 공간 복잡도를 구하세요.

function logUpTo(n) {
    for (var i = 1; i <= n; i++) {
        console.log(i);
    }
}

정답 : O(1)
```

```jsx
아래 함수에 대한 공간 복잡도를 구하세요.

function logAtMost10(n) {
    for (var i = 1; i <= Math.min(n, 10); i++) {
        console.log(i);
    }
}

정답 : O(1)
```

```jsx
아래 함수에 대한 공간 복잡도를 구하세요.

function onlyElementsAtEvenIndex(array) {
    var newArray = Array(Math.ceil(array.length / 2));
    for (var i = 0; i < array.length; i++) {
        if (i % 2 === 0) {
            newArray[i / 2] = array[i];
        }
    }
    return newArray;
}

정답 : O(n) array가커질수록 newArray가 차지하는 공간도 커진다.
```

```jsx
아래 함수에 대한 공간 복잡도를 구하세요.

function subtotals(array) {
    var subtotalArray = Array(array.length);
    for (var i = 0; i < array.length; i++) {
        var subtotal = 0; // O(1)
        for (var j = 0; j <= i; j++) {
            subtotal += array[j]; //O(1) subtotal 값이 변할 뿐 할당하는 공간 자체가 커지진 않기 때문
        }
        subtotalArray[i] = subtotal; //O(n)
    }
    return subtotalArray;
}

정답 : O(n) 
```

# 로그와 섹션 요약

![Untitled](https://user-images.githubusercontent.com/48678872/165692365-0b07669a-7ea0-4f33-a63f-eeef5ca566cc.png)

이진 로그는 1이 되기 전까지 숫자를 2로 나눌 수 있는 횟수를 의미한다. 

![Untitled](https://user-images.githubusercontent.com/48678872/165692461-017c84d8-b911-43b0-a904-62d997e4b62b.png)

총 3번 나눌 수 있다. 따라서 log(8) = 3 이다.

그래서 로그 개념은 언제 나오나?

1. 탐색 알고리즘
2. 정렬 알고리즘
3. 재귀 함수

위의 알고리즘에 대해서는 앞으로 차차 배워보도록 하자.

![harry](https://user-images.githubusercontent.com/48678872/165693037-ee593fbd-8d31-4fb2-8c65-1b130c578f93.PNG)*출처: https://www.bigocheatsheet.com/*
