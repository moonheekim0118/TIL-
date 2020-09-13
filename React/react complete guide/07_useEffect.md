# useEffect in Hooks

- useEffect는 componentDidMount와 componentDidUpdate를 합쳐놓은 것

```javascript
useEffect(()=>{
    setTimeout(()=>{
        alert("Saved data!")
    },1000)
},[props.persons]) 
```

- useEffect에다 배열인자를 넣음으로써 해당 인자가 변할때만 useEffect가 실행되도록 컨트롤 할 수 있다.
- 배열인자에 [] (empty array)를 넣으면 useEffect가 '가장 처음 렌더링 될 때'만 실행된다.