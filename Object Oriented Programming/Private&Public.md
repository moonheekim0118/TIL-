# how to create Private member

### using Closure

```javascript
function ConstructorCar(initValue){
    this.publicMember = initValue;
    let _privateMember = initValue;
    this.getPrivateMember = function(){ return _privateMember}
    this.setPrivateMember = function(v){  _privateMember = v;}
} // getter 와 setter를 이용해서만 접근 가능하다.

ConstructorCar.prototype.drive=function(){
    console.log(this._privateMember) // undefiend
     console.log('Drive!'+this.getPrivateMember()); // 정상출력 
}
```

### in Classes

```javascript
class ClassCar {
 constructor(mileage) {
   this.mileage = mileage; //this is public
   var privateMember = mileage;//this is private
   this.getPrivateMember = function() { return privateMember; }
   this.setPrivateMember = function(v) { privateMember = v; }
 }
    // getter 와 setter를 이용해서만 접근 가능하다.
```

### Factories

```javascript
let FactoryCarProto = (function(){
    var mileage = 0;
    var _privateMember = 0;
    const FactoryCarProto = {
        mileage,
        setMileage(m){
            this.mileage=m;
        },
        drive(){
            this.mileage++;
            console.log('Drive!');
        },
        setPrivateMember(v){
            _privateMember=v;
        },
        getPrivateMember(){
            return _privateMember;
        }
    };
    return FactoryCarProto;
})();

function factoryCar(){
    return Object.create(FactoryCarProto);
}

const car = factoryCar();
```







[reference](https://medium.com/javascript-in-plain-english/private-member-in-javascript-class-2359ef666aaf)

