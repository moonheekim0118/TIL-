# clean up works



## in Class Component - componentWillUnmount	

- 해당 컴포넌트가 remove 되기 전에 실행된다.



## in Hooks - UseEffect() return~

```javascript
useEffect(()=>{
    console.log('[Cockpit.js] useEffect');
    return()=>{
        console.log("removed!");
    }
})
```

- useEffect에서 익명함수를 return 해주면, 해당 컴포넌트가 사라질 때 (업데이트 될 때) 해당 익명함수가 실행된다.
- useEffect 두번째인자로 아무것도 넣지 않으면, return 문의 익명함수는 모든 re-render 시에 실행된다.
- useEffect 두번째인자로 [] 를 넣으면 컴포넌트가 사라질 때 return 문의 익명함수가 실행된다.
- useEffect의 두번째 인자로 특정 props나 state를 넣으면, 해당 props 혹은 state가 업데이트(리렌더) 될 때마다 return문의 익명함수가 실행된다.



### unmount될 때 setTimeout

- unmount될 때 setTimeout을 clearTimeout을 해주어야 한다.