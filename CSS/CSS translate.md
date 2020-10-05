# translate 

- CSS에서 레이아웃의 가운데에 놓고싶을 때

```javascript
.center p {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
```



## transform 속성

- html 엘리먼트의 위치를 변경시킬 수 있다.



### translateX(10px)

- 해당 엘리먼트를 10px만큼 오른쪽으로 이동시킨다. (왼쪽 기준)
- translateX(-10px) 이라고하면 반대편에서 해당 엘리먼트를 10px만큼 왼쪽으로 이동시킨다. (오른쪽 기준)



### translateY(50px)

- 해당 엘리먼트를 50px만큼 아래로 이동시킨다. (위를 기준)
- translateY(-50px) 역시 반대편에서 해당 엘리먼트를 50px만큼 위로 이동시킨다.(아래를 기준)





## 상대적 위치 정하기

- 퍼센트로 상대적 위치를 정할 수 있다.
- 여기서 x는 width를 기준, y 는 height을 기준으로 한다.
- 예를들어 엘리먼트의 width가 500px일때 translateX(%100)은 translateX(500px) 과 같다.