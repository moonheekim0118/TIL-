## DOM

- Document Object Model : 자바스크립트 Node 개체의 계층화 된 트리
- 브라우저는 HTML코드를 해석하여 트리 형태로 구조화된 노드들을 가지고 있는 문서(DOM)을 생성함



## DOM Tree

- 모든 엘리먼트는 HTMLElement의 자식이다. 따라서 HTMLElement의 프로퍼티를 똑같이 가지고 있음
- 또한, 엘리먼트의 성격에 따라서 자신만의 프로퍼티를 가지고 있기도 함

![](https://web.stanford.edu/class/cs98si/img/dom_types.png)

## HTMLElement 객체

- document.getElementById - 리턴 데이터 타입은 HTMLElement (실행결과 하나)
- document.getElementByTagName - 리턴 데이터 타입은 HTMLCollection (실행결과 복수)



## Element의 종류에 따라 리턴 되는 객체가 다르다.

- 즉 엘리먼트의 종류에 따라서 프로퍼티가 다름

1. HTMLLIElement
2. HTMLAnchorElement
3. HTMLInputElement



## HTMLCollection

- 리턴 결과가 복수인 경우
- 유사배열 

