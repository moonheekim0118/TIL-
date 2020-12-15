# Flexbox 헷갈리는 것 정리 



## justify-content

- **flex-direction이 row** 일 경우, 요소들을 **열(column) 기준**으로 정렬한다.
- **flex-direction이 column**일 경우 , 요소들을 **행(row) 기준**으로 정렬한다. 



<br/>

## align-items와 align-content에 대해서

### 공통점

- 둘다 cross-axias를 기준으로 한다. 즉, flex-direction이 row일 경우 행(row) 을 기준으로, column일 경우 열(column)을 기준으로 한다. 



<br/>



### 차이점

- align-items :  **flex line을 기준으로 아이템들을 정렬**한다. 
- align-content : **flex line을 정렬**한다. 즉, flex-line이 여러개 일 때 ( 요소가 여러개로 겹쳐질 때 - 즉 flex-wrap속성이 nowrap이 아닐 때) 해당 flex line들을 정렬한다. 물론 wrap 일경우 align items도 적용 가능하다 .