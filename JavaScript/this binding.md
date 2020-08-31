# this binding  

### 명시적 this바인딩이 없는 한 

- 전역 공간에서 this는 전역객체를 참조한다.
- 어떤 함수를 메서드로 호출한 경우 this는 호출 주체 (메서드명 앞의 객체)를 참조한다.
- 어던 함수를 함수로서 호출한 경우 this는 전역객체를 참조한다. 메서드 내부 함수에서도 같다.
- 콜백 함수 내부에서 this는 해당 콜백 함수의 제어권을 넘겨받은 함수가 정의한 바에 따르며, 정의하지 않은 경우는 전역객체를 참조한다.
- 생성자 함수의 this는 생성될 인스턴스를 참조한다.



### 명시적 this 바인딩

- call, apply 메서드는 this를 명시적으로 지정하면서 함수 또는 메서드를 호출한다.
- bind 메서드는 this 함수에 넘결 인수를 일부 지정해서 새로운 함수를 만든다.
- 요소를 순회하면서 콜백 함수를 반복 호출하는 내용의 일부 메서드는 별도의 인자로 this를 받을 수 있다. (map, forEach , some, every ... )




