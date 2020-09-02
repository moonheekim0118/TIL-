### 컴포넌트 내에서 method binding 해주기

```react
    constructor(props){
        super(props);
        this.state = {
            result:'',
            value:'',
            answer:getNumbers(),
            tries:'',
        };
        this.onSubmitForm=this.onSubmitForm.bind(this);
        this.onInputChange=this.onInputChange.bind(this);
    }
    onSubmitForm(e){}

    onInputChange(e){
        this.setState(value, e.currentTarget.value);
    }
```

- 새로 생성한 메서드에 대하여 해당 컴포넌트를 this로 바인딩하고 싶다면 constructor 내에서 props를 super로 넘기고, 메서드를 바인딩 해준다. 
- 위와 같은 과정을 생략한게 최신문법 (ES6) 화살표함수인데, 화살표함수는 알아서 this binding을 해주므로, constructor 자체가 필요 없다.