# 'use strict'

```javascript
function weird(){
	height=50;
	return height;
}

weird(); // error 없이 50 반환
```

- 자바스크립트는 위와같은 경우에 global에서 height을 알아서 정의해주므로 에러가 나지 않는다.
- 이를 방지하기 위해서는 코드의 맨 위에 'use strict'를 입력하면 된다.

