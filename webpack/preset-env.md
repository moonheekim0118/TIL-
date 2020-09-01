# @babel/preset-env

- preset = plugin들의 모음
- preset-env == 자동으로 예전 브라우저 지원해주는 기능
- preset-react == 리액트 지원 
- 따라서 각 plugin에 대한 설정을 해야 하는 경우도 있음

```javascript
loader: 'babel-loader',
options: {
    presets:[
        ['@babel/preset-env',{
            browsers:['last 2 chrome versions'] // 브라우저 설정 가능 
        }] // 설정 내용 작성
    ],
        plugins:[]
}
```

- preset env에서 브라우저 설정은 해주는게 좋다!
  - 안그러면 바벨이 하는일이 많아져서 용량이 무거워짐 