# Inheritance

```javascript
class Character{
    constructor(name,weapon){
        this.name=name;
        this.weapon=weapon;
    }
    attack(){
        return 'attack with'+ this.weapon;
    }
}

class Elf extends Character{
    constructor(name,weapon,type){
        super(name,weapon); // call the super class 
        this.type=type;
    }
}

class Orge extends Character{
    constructor(name,weapon,color){
        super(name,weapon);
        this.color=color;
    }
    makeFort(){
        return 'fort!!';
    }
}

const dobby = new Elf('dobby', 'cloth', 'house elf');
const shrek = new Org('shrek', 'club', 'green');
```

- 새로운 constructor를 정의할 때는 super 부터 호출해주어야 한다.

![](https://raw.githubusercontent.com/moonheekim0118/TIL-/master/Object%20Oriented%20Programming/%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85.png)

- 자바스크립트에서 상속은, 정말로 클래스를 복사하는 것이 아니라, 프로토타입으로 link 하는 것을 말한다. 여기서 Character를 상속한 Elf와 Orge의 prototype은 Character 가 된다.  