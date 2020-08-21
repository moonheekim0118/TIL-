# inline Caching - complier 

```javascript
function findUser(user){
    return `found${user.firstName} ${user.lastname}`;
}

const userData{
    firstName :'Lisa'
    LastName :'Simpson'
}

findUser(userData);  --- > 'found Lisa Simpson' 으로 대체 
```

- 같은 메서드를 반복하는 코드는 인라인 캐싱을 입력하여 메서드 자체를 값으로 대신한다. 





# Hidden Classes

```javascript
function Animal(x,y){
    this.x =x;
    this.y=y;
}

const obj1 = new Animal(1,2);
const obj2 = new Animal(3,4);

obj1.a= 30;
obj1.b= 100;
obj2.b= 30;
obj2.a = 100; 
```

- obj1과 obj2는 같은 프로퍼티를 가진 hidden class를 가지는데, 두 obj의 프로퍼티 값을 바꾸면 (x , y가 아니라 a b)  컴파일러는 hidden class가 아님을 감지하고 분리한다 -> 느려짐 



