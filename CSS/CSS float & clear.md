# float & Clear

### float

- 컨텐츠 포지셔닝에 쓰이며, 해당 컨텐츠가 **컨테이너 기준**으로 어디에 포지션 되어야 할지 정할 수 있다.
- left : 해당 element가 컨테이너의 왼쪽에 위치한다.
- right : 해당 element가 컨테이너의 오른쪽에 위치한다.
- none : default / float되지 않고 마크업 된 곳에 위치
- inherit : 부모의 float value를 물려받는다.



### clear

- float 한 속성 주위로 다른 element가 따라 붙지 않게 하는 property
  - 예를 들면 사진 위주로 글자가 따라 붙지 않게 하는 것
- 따라서 float을 left로 했다면 clear 역시 left로, right이면 right으로 해줄 수 있고 both도 있다.



### clearfix hack

- float 한 element가 해당 컨테이너보다 크기가 크다면, 해당 컨테이너 바깥으로 overflow된다.
- 바깥으로 overflow 되는 것을 방지하기 위해서는 컨테이너의 overflow 속성을 auto로 해주면 된다.