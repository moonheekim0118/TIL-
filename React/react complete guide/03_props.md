# section3 props		

### Props를 이용해 동적 데이터 띄우기

```javascript
class App extends Component {
  render(){
    return (
      <div className="App">
        <h1>hellloooo</h1>
        <Person name="moonee" age="23" />
        <Person name="Boogie" age="6"> and Im soo cutee...</Person>
      </div>
    )
  }
}
export default App;

```

```javascript
const person = (props)=>{
return (<div>
    <p> Im a {props.name}~ and im {props.age}olds</p> 
    <div>{props.children}</div>
</div>)
}

```

- <>태그 내부에 있는 요소들은 props.children으로 접근 가능



