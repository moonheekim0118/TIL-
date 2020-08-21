# JavaScript Engine

![](https://miro.medium.com/proxy/1*ZIH_wjqDfZn6NRKsDi9mvA.png) 

### Interpreter

- line by line으로 읽어서 코드를 해석한다.
- 코드 해석 할 때, 컴파일러와 다르게 optimization 과정이 없어서 느리다. 
  - optimization : 실행 시간과 메모리를 줄이기 위해서 코드의 요소들을 최소화하거나 최대화하는 것. 예를들면 for loop에서 같은 함수를 100번이상 호출 할때, 말 그대로 100번동안 해당 함수를 호출하는게 아니라 한번만 호출 한후에 그 값을 100번 실행하는 것

### Compiler 

- 코드 전체를 읽어들여서 아예 다른 코드로 변환시키는 것
- 초기 set up이 매우 느리지만, optimization이 있어서 interpreter보다 빠를 수 있다.
- babel은 ES5이상의 자바스크립트 코드를 읽어들여서 구버전 자바스크립트 코드로 변환 시키는 컴파일러이다.





### JIT Compiler in V8 (Just In time)

- Interpreter가 코드를 Bytecode로 해석함
- Bytecode로 해석한 내용중에 optimize할 게 있나..Profiler가 살펴봄
- optimize할 게 있으면 Compiler에게 넘겨줌
- 그러면 Compiler가 compile하거나 수정하여 optimization 하여 optimized code를 뱉어냄



### JavaScript is Interpreted Language ?

- 예전에는 bytecode를 브라우저에 넘겨주는게 다였지만 V8이후 컴파일도 함 
- Technically, It depends on Implementation of JavaScript Engine





