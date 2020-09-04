# Box sizing

- 기본적으로 box의 width와 height은 padding과 border를 따로 계산하게된다.
- 따라서 우리가 지정한 width와 height보다 더 크게 박스 사이즈가 잡힐 수 있다.
- 이를 방지하기 위해 box sizing을 border box로 설정해주어야 한다.

####  border box

- border box로 설정해주면, padding과 border의 사이즈가 박스 사이즈 자체에 포함되기 때문에 우리가 원하는 대로 박스의 크기가 지정된다.