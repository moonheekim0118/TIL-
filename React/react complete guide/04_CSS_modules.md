# CSS Modules

- react script 2 이상에서는 지원해줌
- 사용하기 위해서는 CSS 파일 확장자명을 .module.css 로 바꿔줘야한다.

```css
.Button {
  background-color: green;
  color:#fff;
  border:1px solid blue;
  padding:8px;
  cursor: pointer
}

.Button:hover{
  background-color: lightgreen;
  color:black
}

.Button.Red{
  background-color: red;
}

.Button.Red:hover{
  background-color: salmon;
}

```



```javascript
import styles from './App.module.css';
let btnClass =[styles.Button];
btnClass.push(styles.Red);
<button className={btnClass}/>

```

