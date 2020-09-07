# Passing Method References Between Components

- method들 다른 컴포넌트에 넘겨주기 위해서는 this binding을 거쳐야한다.
  - bind 해주지 않으면, 해당 메서드 내에서 this가 undefined 됨 

- 첫번째 방법 : bind를 이용하기

```javascript
 <Person click={this.swtichNameHandler.bind(this,'매서드 매개변수')}/>
```

- 두번째 방법 : Arrow function 이용

```javascript
 <Person click={()=>this.swtichNameHandler('매서드 매개변수')}/>
```



- 두번째 방법은 매우 비효율적이므로 왠만하면 bind 쓰기 