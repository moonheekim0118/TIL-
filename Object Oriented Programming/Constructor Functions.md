# Constructor Functions

```javascript
function Elf(name, weapon){
    this.name=name;
    this.weapon =weapon;
}

Elf.prototype.attack(){
    return `attack with%{this.weapon}`;
}
const Mel = new Elf('Mel', 'stones');
```

- 자바스크립트에서는 '함수' 에만 prototype이 있으므로, function을 생성해주고 prototype에 여러 메서드를 넣어줌으로써 '클래스' 처럼 보이게 해준다



```javascript
Elf.prototype.build(){
    function building(){
        return this.name;
    }
    return building();
}
```

- 메서드 내부에 inner function을 선언하면, 해당 function은 object에 속하는게 아니라 window에 속하게 되어 해당 메서드를 호출하면 undefined가 return 된다.

#### 해결방법

```javascript
Elf.prototype.build(){
    function building(){
        return this.name;
    }
    return building.bind(this);
} // 바인드 이용 

Elf.prototype.build(){
    const self = this;
    function building(){
        return self.name;
    }
    return building();
} // 클로저에 this 담아줘서 참조하기 
```

