# ref

- DOM에 직접 접근하고 싶을 때
  - ex) 특정 state가 변화될 시, input에 focust를 주고싶다!
- 컴포넌트에 해당 변수를 따로 선언해주어서 this.변수 로 접근하여 변화시키면 된다!



```javascript
<input ref={(c)=>this.input=c}type="number" value={this.state.value} onChange={this.onChange}/> // 여기서 input은 클래스내 해당 변수 이름!
```

```javascript
this.input.focus();
```



