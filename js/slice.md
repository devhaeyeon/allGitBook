# slice

{% embed url="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/slice" %}

해당 문서를 참고하였습니다.

어떤 배열의 begin부터 end까지\(end는 불포함\)에 대한 shallow copy\(얕은 복사\)를 새로운 배열 객체로 반환함.

원본 배열은 수정되지 않는다. 

**구문**

arr.slice\(\)

arr.slice\(begin\)

arr.slice\(begin, end\)

**매개변수**

-begin

0을 시작으로 하는 추출 시작점에 대한 인덱스를 의미함.

음수 인덱스는 배열의 끝에서 부터 길이를 나타냄.

-end

추출을 종료할 0기준 인덱스. 

slice는 end인덱스를 제외하고 추출함.

음수 인덱스는 배열과 끝에서 부터 길이를 나타냄.

end가 생걀되면 slice 는 배열의 끝까지\(arr.length\)를 추출함

만약 end값이 배열의 길이보다 크다면, slice는 배열의 끝까지\(arr.length\)을 추출함.

**반환값**

추출된 요소가 포함된 새로운 배열

설명

원본을 대체하지 않음. 원본 배열에서 요소의 얕은 복사본을 반환함.

원본 배열 요소는 

객체 참조\(및 실제 객체가 아님\)의 경우 slice는 객체 참조를 새 배열로 복사함.

원본 배열과 새 배열은 모두 동일한 객체를 참조함.

참조된 객체가 변경되면 변경 내용은 새 배열과 원래 배열 모두 볼 수 있음 .

String 및 Number객체가 아닌 문자열과 숫자의 경우 slice는 문자열과 숫자를 새 배열에 복사함. 한 배열에서 문자열이나 숫자를 변경해도 다른 배열에는 영향을 주지 않음.

새 요소가 두 배열 중 하나에 추가되면 다른 배열은 영향을 받지 않음.

```javascript
var arr = [
  { id: 1 , subTitle:'제목1' },
  { id: 2 , subTitle:'제목2' },
  { id: 3 , subTitle:'제목3' },
  { id: 4 , subTitle:'제목4' },
  { id: 5 , subTitle:'제목5' },
  { id: 6 , subTitle:'제목6' },
  { id: 7 , subTitle:'제목7' },
  { id: 8 , subTitle:'제목8' },
];

var arrNewList = arr.slice(4,8);

console.log(arrNewList);
console.log(arr);
```

어떤 곳에 사용되는지 생각을 해보면

기존의 배열을 가지고 와서 새로운 배열을 만들때, 

게시글의 페이징 같은 걸 구현한다고 했을 때 어떤 부분부터 어떤 부분까지 불러올 때가 

아닐까 싶습니다. 

하지만 filter와 동일하게 새로운 배열을 만들어 내므로 기존 배열에 대한 값 유지는 가능해집니다. 





