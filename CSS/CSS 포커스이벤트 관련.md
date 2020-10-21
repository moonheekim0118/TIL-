# Trouble Shooting

- div 엘리먼트에 focus 효과를 주고싶다면 div 에 tabindex="0" 아트리뷰트를 선언하자!
- 특정 Input이 focus 되었을 때 뜨는 창이, 해당 창 내부를 눌러도 안없어지게 하고싶다면 ? (모달창처럼)
  - 이 경우는 디폴트 display가 none으로 되어있어서 특정 input focus 이벤트가 사라지면 바로 display none으로 되어서 어떤 click 이벤트도 먹히지 않음
  - 이를 위해서는  해당 창에 hover 이벤트 => display:block 효과를 주고, 그 후 focus이벤트 => display:block 효과를 주면 된다. 

```css
    &:hover{
        display:flex;
    }

    &:focus-within{
        display:flex;
    }
```

