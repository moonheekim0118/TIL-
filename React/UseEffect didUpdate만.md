```javascript
const mounted = useRef(false);
useEffect(()=>{
    if(!mounted.current){
        mounted.current=true;
    }
    else{
        // ajax
    }
},[바뀌는 값])
```

- didUpdate에서만 실행되도록 하는 꼼수(?)
- didMount에서는 실행되지 않음