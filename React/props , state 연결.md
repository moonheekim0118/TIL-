# Props - state 연결

- props를 물려받은 자식은 props의 내용을 변경 하지 않도록 하자!
  - 자식이 props를 바꾸면 부모의 내용이 뜻하지 않게 바뀌게 된다. 
- 변경하고싶다면 해당 props를 state로 설정하자!

```javascript
const Try = memo(({tryInfo})=>{
    const [result,setResult]=useState(tryInfo.result);
})
```

