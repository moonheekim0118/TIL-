```javascript
 this.setState({result:`${this.state.num1}*${this.state.num2}=${this.state.value} 딩동댕쓰~~`,
num1: Math.ceil(Math.random()*9),
num2: Math.ceil(Math.random()*9),
 value:''
}) 
```

- 위와 같이 setState, 즉 state를 바꾸는 메서드 내에 this.state를 출력하면 헷갈린다. 따라서 setState에다 새로운 state를 return 해주는 함수를 넣어준다.
- prevState를 통해 예전 상태 값에 보다 정확하게 접근가능
- setState는 비동기함수 



```javascript
this.setState((prevState)=>({result:`${preveState.num1}*${prevState.num2}=${prevState.value} 딩동댕쓰~~`,
num1: Math.ceil(Math.random()*9),
num2: Math.ceil(Math.random()*9),
value:''
})) 
```



- setState 할 때 redner함수는 다시 실행된다.