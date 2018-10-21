# javascript assign vs jquery extend

extend는 객체를 merge할 때도 사용하고, 복사를 사용할 때도 사용합니다. 

\(주로 복사를 할 때 사용합니다.\)

{% embed url="https://gomakethings.com/vanilla-javascript-version-of-jquery-extend/" %}

{% embed url="https://www.pixelstech.net/article/1477888746-Deep-clone-of-JavaScript-object" %}

객체를 merge 할 때 jquery에서는 extend를 사용하고 javascript에서는 assign을 한다고 한다. 

그리고 객체의 복사에는 shallow copy, deep copy가 있는데

shallow copy는 객체의 레퍼런스만 복사를 하고,

deep copy는 객체의 레퍼런스, 컨텐츠들을 복사를 합니다. 

jquery의 extend는 shallow copy를 하고

javascript의 assign은 deep copy를 합니다. 







