# Debouncing & Throttling



- 디바운싱
  - 연이어 호출되는 함수들 중 마지막 함수( or 제일 처음 함수) 만 호출 하도록 하는 것
  - ajax 검색에 자주 쓰임 
- 쓰로틀링
  - 마지막 함수가 호출 된 후 일정 시간이 지나기전에 다시 호출되지 않도록 하는 것
  - 스크롤 이벤트에 자주 쓰임 



## Debouncing

- 검색어창에 엔터 없이도 결과를 보여주는 것 
- 이를 위해서는 input 이벤트에 대기하고 있어야함

```javascript
document.querySelector('#input').addEventListener('input', (e)=>{
    console.log('ajax 요청~', e.target.value);
})
```

- 문제점 : 한글자 칠 때마다 ajax 요청이 실행된다는 것
- 따라서 글자를 다 쳤을 때만 ajax 요청을 보내고 싶을 때 디바운싱을 사용 할 수 있다.



### How ?

- 타자를 칠 때 (input 이벤트가 발생 할 때) 마다 타이머를 설정한다.
- 200ms 동안 입력이 없으면 입력이 끝난 것으로 간주한다. --> 이제서야 ajax 요청을 보낸다. 
- 200ms 이전에 타자 입력이 발생하면 이전 타이머는 취소하고 새로운 타이머를 다시 설정한다.

```javascript
var timer;
document.querySelector('#input').addEventListener('input', (e)=>{
    if(timer){
        clearTimeout(timer); // 200ms 이전에 타자 입력이 발생 시, 이전 타이머 취소하고 새로운 타이머 설정 
    }
    timer = setTimeout(()=>{ // 200ms 동안 입력이 없으면 입력이 끝난 것으로 간주하고 ajax 요청 보낸다. 
        console.log('ajax 요청~', e.target.value); // ajax 요청 
    }, 200); 
})
```



<br/>

<br/>



## Throttling

- 스크롤을 올리거나 내릴 때, scroll 이벤트가 매우 많이 발생함
- scroll 이벤트가 발생 시 복잡한 작업을 하도록 설정했다면 성능 저하가 심각해짐
- 따라서 쓰로틀링을 이용하여 , 몇초에 한번, 또는 몇밀리초에 한번씩만 실행되게 제한을 둔다.





### ajax 요청 예제를 쓰로틀링으로 변경

- 200 밀리초마다 요청을 보낸다.
- 이미 타이머가 설정되어 있다면 아무 동작도 하지 않음.
- 타이머가 설정되어있지 않다면, 타이머를 설정하고, 해당 타이머를 일정 시간 후에 해제한 후,  ajax 요청을 날린다. 

```javascript
var timer;
document.querySelector('#input').addEventListener('input',(e)=>{
    if(!timer){
        timer= setTimeout(()=>{
            timer=null;
             console.log('ajax 요청~', e.target.value);
        },200)
    }
})
```

