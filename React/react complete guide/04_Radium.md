# Radium 이용해 pseudo selector, 미디어쿼리 적용하기

```javascript
npm install --save radium
```



### pseudo selector

```javascript
import Radium from 'radium';
 const style={  // inline 방식으로 CSS 적용 
       border:'none',
      backgroundColor: 'aquamarine',
      padding: '5px 16px',
      fontSize:'1rem',
      borderRadius: '5px',
      cursor: 'pointer',
      ':hover':{
        backgroundColor:'lightgreen'
      }
    
// style요소 변경시
 style[':hover']={
        backgroundColor:'white'
      }
```

```javascript
export default Radium(App);
```



### 미디어 쿼리

```javascript
    const style={
        '@media(min-width:500px)':
        {
            width:'450px'
        }
    }
```

- App 컴포넌트를 < StyleRoot > 로 감싸주기

```javascript
import Radium, {StyleRoot} from 'radium';
    return (
      <StyleRoot>
      <div className="App">
        <h1>hellloooo</h1>
        <button style={style} onClick={this.togglePersonsHandler} className="changBtn">Toggle Persons</button>
        {persons}
      </div>
      </StyleRoot>
    )
  }
```

