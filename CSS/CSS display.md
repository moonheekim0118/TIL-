# CSS display 

### inline

- 전후 줄바꿈 없이 한 줄에 다른 엘리먼트들과 나란히 배치된다.
- **width와 height 속성을 지정해도 무시**된다. 왜냐하면, 해당 태그가 마크업 하고 있는 컨텐츠 크기 만큼만 공간을 차지하도록 되어있기 때문
- **margin paddding 속성은 좌우 간격만 반영되고 상하 간격은 반영되지 않는다.**



### block

- 전후 줄바꿈이 들어가 다른 엘리먼트들을 다른 줄로 밀어내고 혼자 한줄을 차지 한다. 
- width, height, margin, padding 속성이 모두 반영된다.



### inline-block

- 기본적으로 inline 엘리먼트 처럼 전후 줄바꿈 없이 한 줄에 다른 엘리먼트들과 나란히 배치된다. 하지만 **width와 height 속성 지정 및, margin padding의 상하 간격 지정이 가능**해진다.
- 대표적인 inline block 엘리먼트로 **button과 select 태그**가 있다