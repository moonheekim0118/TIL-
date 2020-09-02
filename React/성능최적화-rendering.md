

# 렌더링 성능 최적화

- 리액트는 실제 props 나 state 내용이 변경되지 않아도, setState가 호출되면 렌더링이 일어난다.
- 이를 방지하기 위해 직접 설정해주어야 한다. 

### 방법 1 . shouldComponentUpdate

```javascript
shouldComponentUpdate(nextProps, nextState, nextContext){
    if(this.state.counter!==nextState.counter){ return true}
    return false;
}
```

### 방법 2 . PureComponent

```javascript
class Test extends PureComponent {...}
```

- shouldComponentUpdate를 자동으로 구현해놓은 것
- state가 바뀌었는지 확인
- 주의점
  - 참조관계가 있는 구조 (배열, 객체)에서는 push 와 같은 내장 메서드에 의한 값의 변화를 알아차리지 못한다. (일반 컴포넌트와 마찬가지)



### Hooks  - React.memo

```javascript
const func = memo() =>{...}
```

