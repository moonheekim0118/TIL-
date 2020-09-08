# Styled Components

```javascript
npm install --save styled-components
```

```javascript
import styled from 'styled-components';
```

- style을 추가하고 싶은 요소에 대하여 div / button 등의 style 컴포넌트 정의

```javascript
const StyleBtn= styled.button`
    background:${props => props.alt ? 'red' : 'green'};
    padding: 5px 15px;
    border:none;
    color:#fff;
    border-radius:5px;
    cursor:pointer;

    &:hover{
      color:${props => props.alt ? 'red' : 'green'};
      background:#fff;
      border: 1px solid ${props => props.alt ? 'red' : 'green'};
    }

    &:focus{
      outline:none;
    }
  
`

const StyleDiv =  styled.div`
  width:60%;
  margin: 16px auto;
  text-align:center;

@media(min-width:500px)
{
  width:450px;
}
`
```

- 정의한 StyleBtn과 StyleDiv를 기존 div, button 태그처럼 아래와 같이 JSX에 사용해주면 된다.

```javascript
 <StyleDiv>
  <StyleBtn alt={this.state.showPersons} onClick={this.togglePersonsHandler} className="changBtn">Toggle Persons</StyleBtn>
</StyleDiv>
```

- alt 키워드를 이용하여 동적으로 내부 요소를 변경할 수 있다.

```javascript
background:${props => props.alt ? 'red' : 'green'};
```

