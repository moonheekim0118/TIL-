# useMemo와 useCallback	

- ### useMemo는 특정 함수의 결괏값을 저장해놓을 수 있다.

  - Hooks의 경우 렌더링할 때 전체함수가 재실행되므로 복잡한 함수가 계속 실행될 여지가 있다.
  - 이러한 함수의 결과값을 useMemo에 저장해준다면, 해당 함수를 계속 호출하지 않을 수 있다.
  - useRef와 다른점은 ref는 일반값을 저장한다는 것이고, useMemo는 복잡한 함수의 결괏값을 저장한다는 것이다.



```javascript
 const LottoNumbers = useMemo(()=>getWinNumbers(),[]);
 const [winNumbers, setWinNumbers] = useState(LottoNumbers);
```



- ### useCallback은 함수 자체를 저장해놓을 수 있다.

```javascript
    const onClickRedo= useCallback(()=>{
        console.log('onClickRedo');
        setWinNumbers(getWinNumbers());
        setWinBalls([]);
        setBonus(null);
        setRedo(false);
        timeouts.current=[];
    })
```

- 이렇게하면 함수 컴포넌트가 재실행되어도 해당 함수가 새로 생성되지 않는다.
- 하지만, 문제점은 바뀌여야할 state가 바뀌지 않는다. 이를 방지하기 위해서는 input에다 useCallback 함수 내에서 setState로 변경되는 state를 넣어주어야 한다.



```javascript
    const onClickRedo= useCallback(()=>{
        console.log('onClickRedo');
        setWinNumbers(getWinNumbers());
        setWinBalls([]);
        setBonus(null);
        setRedo(false);
        timeouts.current=[];
    },[winNumbers])
```

- 이렇게 input에 state를 넣으면, 해당 state가 변경될 시 해당 함수가 새로 생성된다.
- 자식 컴포넌트에 함수를 넘길 때는 해당함수에 useCallback을 무조건 적용시켜야함. 그러지 않으면 매번 새로운 함수가 생성되어서 계속 새로운 함수가 props로 넘겨짐 -> 따라서 계속 새로 렌더링을함..







#### input값에 특정 값을 넣어주면, 해당 값이 변경될 시 useCallback혹은 useMemo가 새로 생성된다

