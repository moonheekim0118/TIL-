# vh, vw 단위

- 뷰포트의 너비값과 높이값에 으지ㅗㄴ
- vh 요소는 높이값의 1 /100 단위
- 즉 브라우저 높이 값이 900 px일 때, 1vh는 9px이라는 듯이고, 뷰포트의 너비값이 750px일 때 1vw는 7.5px이 된다.
- font-size에도 적용 가능



# vmin & vmax

- 뷰포트의 너비값과 높이값에 따라 최대, 최소값을 지정할 수 있다.
- 예를들어 브라우저의 크기가 1100px width이고 높이가 700px height일 때, 1vmin은 7px이 되고 1vmax 는 11px이 된다. 
- 터치화면 양변에 가득차는 정사각형 요소를 만들 때 활용 가능



```css
.box{
    width:100vmin;
    height:100vmin;
}
```



- 혹은 양옆은 넘치지 않고 위아래 스크롤만 가능하게 하려면

```css
.box{
    width:100vmin;
    height:100vmax;
}
```

