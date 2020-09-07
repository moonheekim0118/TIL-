# section3 understanding jsx

```javascript
import React, {Component} from 'react';
import './App.css';

class App extends Component {
  render(){
    return (
      <div className="App">
        <h1>hellloooo</h1>
      </div>
    )
  }
}

export default App;

```

- render에서 return 해주는 jsx코드는 자바스크립트로 컴파일 되고, 리액트가 내부에서 html로 변환시켜준다. 
- 해당 코드는 아래와 같이 React 모듈을 통해 컴파일된다.



```javascript
return React.createElement('div',{className: 'App'}, React.createElement('h1',null,'heelllooo'));
```

## Restrictions in JSX

### 1. className

- 자바스크립트의 class 키워드와 겹치기 때문에 jsx 내에서는 class대신 className을 쓴다.

### 2. must have one root element

- 하나의 root element 를 쓰는 것이 관용적이다.



