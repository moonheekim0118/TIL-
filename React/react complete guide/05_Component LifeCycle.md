# Component lifecycle

### Creation

1. **constructor** 
   - Default ES5 class Feature
   - props를 받기때문에 super(props)를 호출해야함
   - 내부에서 진행 할 수 있는 것
     - state 설정
   - 내부에서 진행 하면 안되는 것
     - side effect이 있는 것들
     - HTTP 리퀘스트 보내기
     - localStorage에 저장하기
2. **getDerivedStateFromProps (props,state)**
   - 물려받은 props가 변경될 시 state 업데이트 (거의 안씀)
3. **render()**
   - JSX 코드 
   - setTimeout이나 HTTP 리퀘스트와 같이 rendering을 방해하는 것은 금지!
4. **Render Child Components**
   - render에 포함된 다른 rendered component들이 렌더링 된다.
5. **componentDidMount**
   - can cause side effect! 
   - State를 업데이트 해서는 안된다. 업데이트 하고싶으면 모든 비동기 연산이 끝나고 나서! 왜냐하면 다시 렌더링을 해야하기 때문..



### Update

1. **getDerivedStateFromProps (props,state)**
   - 물려받은 props가 변경될 시 state 업데이트 (거의 안씀)
2. **shouldComponentUpdate(nextProps, nextState)**
   - re-render를 계속할지 정할 수 있음
3. **render()**
4. **update child component Props**
5. **getSnapshotBeforeUpdate(prevProps, prevState)**
6. **ComponentDidUpdate**
   - can cause side effect!
   - State를 업데이트 해서는 안된다. 업데이트 하고싶으면 모든 비동기 연산이 끝나고 나서! 왜냐하면 다시 렌더링을 해야하기 때문..



