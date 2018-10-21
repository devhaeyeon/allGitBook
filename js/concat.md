# concat

[http://infosecguide.tistory.com/117](http://infosecguide.tistory.com/117)

\(인자, 인수 차이...\)

파라미로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환함.

{% embed url="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/concat" %}

해당 페이지를 참고하여 정리하였습니다.



**문법**

var newarray = old\_array.concat\(value1\[, value2\[,...\[,valueN\]\]\]\);

**인수\(Arguments\)**

valueN : 새 배열로 합쳐질 배열, 값 

자세한 설명

메서드를 호출한 뒤 배열 뒤에 각 인수를 순서대로 붙인 새 배열을 만듦.

파라미터가 배열이면 그 성분이  순서대로 붙고, 배열이면 그 성분이 순서대로 붙고, 배열이 아니면 그 인수 자체가 붙음.

concat은 this나 인수로 넘겨진 배열의 내용을 바꾸지 않고 대신 주어진 배열들을 합친 뒤 그 것의 얕은 사본\(shallow copy\)을 반환함. 원본 배열의 요소들은 새 배열에 다음과 같은 방법으로 복사됨.

* 실제 객체가 아닌 객체 참조 : concat은 새 배열에 객체 참조를 복사함. 원본 배열과 새 배열에서 같은 객체를 가리키게 됨. 즉, 참조된 객체가 수정되면 그 내용이 새 배열과 원본 배열 둘 다에서 나타남.
* String객체나 Number객체가 아닌 문자열과 수 :  concat은 새 배열에 문자열과 수의 값을 복사함.

\*\* 배열이나 값을 이어 붙여도 그 원본은 변하지 않음. 또 새 배열에 어떤 조작을 가하더라도 원본 배열은 영향을 받지 않음.

1\) 배열 두개 이어 붙이는 예

```javascript
var alpha = ['a', 'b', 'c'],    numeric = [1, 2, 3];var alphaNumeric = alpha.concat(numeric);console.log(alpha);console.log(alphaNumeric); // 결과: ['a', 'b', 'c', 1, 2, 3]
```

2\) 배열 세 개 이어 붙이기

```javascript
var num1 = [1, 2, 3],    num2 = [4, 5, 6],    num3 = [7, 8, 9];var nums = num1.concat(num2, num3);console.log(num1);console.log(num2);console.log(num3);console.log(nums); // 결과: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

3\) 배열 값 이어 붙이기

```javascript
var alpha = ['a', 'b', 'c'];
var alphaNumeric = alpha.concat(1, [2, 3]);console.log(alpha);console.log(alphaNumeric); 
```

4\) 데이터 객체 이어 붙이기

```javascript
var textList = [
	{id:1,subject:'title1'},
	{id:2,subject:'title2'}
];

var addTextList = {
	id:3,subject : 'title3'
};

var newTextList=textList.concat(addTextList);

console.log(newTextList);
console.log(textList);
console.log(addTextList);
```



