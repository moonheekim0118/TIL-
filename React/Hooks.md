# Hooks 

- 기존의 Class 형 컴포넌트를 함수로 변경한 것
- 더 간결하다는 것이 장점
- 리액트에서는 Hook을 사용할 것을 권장하지만, 컴포넌트와 함께 써도 상관 없다.



### 컴포넌트와 다른점

1. state 초기화

```javascript
// 컴포넌트의 경우 state 초기화시, 생성자에서 this.state~ 을통해 초기화했음
this.state={
    value:''
}
// hook에서는 useState 메서드를 사용한다.
const [value, setValue]= React.useState('');
// 사용된 문법은 구조분해 할당 
```

2. setState
   - Hook에서는 모든 state에 대해서 개별적 setState메서드가 주어진다 ( 구조분해 할당)

```javascript
setValue('');
```



3. ref 접근 및 변경

```javascript
const inputRef = React.useRef();

inputRef.current.focuse(); // 변경 
```



### setState 될 때마다 렌더가 되는가 ?

- No! setState 메서드는 비동기이기 때문에 여러번 쓰는 경우 리액트에서 알아서 한번에 처리해줌. 따라서 여러번 setState를 해도 렌더는 한번! 



### 주의점

- 컴포넌트는 state변경시 render 함수만 다시 실행된 반면, Hook은 state변경시 해당 함수 자체가 다시 실행됨 . 따라서 느릴 수 있음

- Hook에서도 컴포넌트와 마찬가지로, setState 시, 이전 state 사용하는 경우 함수를 써주어야 한다.