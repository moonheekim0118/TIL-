# Center elements Horizontally and vertically

### 1. Elements 가운데 정렬하기

- block element를 가운데 정렬하기 위해서는 **margin : auto** 속성을 쓰면 된다.
- 주의점 : 해당 element의 width가 정의되어있지 않거나 100%로 정의된 경우 margin auto 값이 적용되지 않는다.



### 2. Text 가운데 정렬하기

- **text-align: center**



### 3. Image 가운데 정렬하기

- image의 display를 **block level**로 바꾸어준다.
- **margin-left와 margin-right을 auto**로 설정해준다.



### 4. 왼쪽/오른쪽 정렬하기 

#### 1) position

- **position : absolute**를 사용한 후, right과 left를 조정해준다.

#### 2) float

- float right /float left로 설정해준다.



### 5. 세로 가운데 정렬 하기 ( center 컨테이너 내 내부 요소)

#### 1) Padding 

- 컨테이너 내 element를 세로-가운데 정렬하기 위해서는 padding 을 이용해준다.
- text를 세로/가로 모두 가운데 정렬하고 싶다면 padding 적용후 text-align center를 해주면 된다.

#### 2) line-height

- **line height을 height과 동일하게 적용**하면 컨테이너 내 element가 세로 / 가운데 정렬하게 된다. 

```css
.center {
  line-height: 200px;
  height: 200px;
  border: 3px solid green;
  text-align: center;
}

/* If the text has multiple lines, add the following: */
.center p {
  line-height: 1.5;
  display: inline-block;
  vertical-align: middle;
}
```



#### 3) Position & transform

- position을 absolute로 정의해준 후, top과 left를 각각 50%로 해준다.
- 화면의 크기가 변해도 가운데 정렬을 할 수 있도록 **transform : translate(-50%,50%)**를 추가해준다.

```css
.center {
  height: 200px;
  position: relative;
  border: 3px solid green;
}

.center p {
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```



#### 4) FlexBox

```css
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
```

