

## 객체를 만드는 패턴

- 참조
  - (책) 프론트엔드 개발자를 위한 자바스크립트 프로그래밍 : 6장 객체지향 프로그래밍
  - [(Medium) Instantiation Patterns in JavaScript – DailyJS](https://medium.com/dailyjs/instantiation-patterns-in-javascript-8fdcf69e8f9b)



[TOC]

### 0. 객체 리터럴로 만든다. 

```javascript
obj = {
name: Mark,
age: 20,
The
hobby: Dancing
}
```



### 1. 일반 함수로 만든다. (팩터리 패턴)

```javascript
function createPerson(name, age, job) {
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function() {
        alert(this.name);
    };
    return o;
}

```

- 항상 새로운 객체를 만들고 새로운 객체 내의 프로퍼티와 메소드를 수동으로 할당해준다. 
- 한 번 만들어둔 함수를 사용하기에 객체 리터럴로 객체를 정의할 때처럼 매번 코드를 중복해서 쓸 필요는 없다. 
- 단점 : 객체가 어떤 타입인지 알 수 없다. 즉 constructor가 무엇인지 (=어떤 constructor의 instance인지) 알 수 없다.



#### 팩터리 패턴 내에서 프로퍼티/메소드를 할당하는 방식

팩터리 패턴에서도 메소드를 할당하는 방식을 다르게 해 메모리 관리를 효율적으로 할 수 있다. 



##### 1-1) Functional Instantiation

```javascript
var Animal = function(species, name) {
    var obj = {};
    obj.species = species;
    obj.name = name;
    obj.makeSound = function() {
        
    };
    obj.eat = function() {
 
    };
    obj.sleep = function() {
        
    };
    return obj;
}
```

- 함수 내에서 모든 프로퍼티와 메서드를 직접 정의하고 할당한다. 
- 가독성이 좋고 만들기 쉽다. 프로퍼티들이  private하다.
- 단점 : 해당 상성자를 활용해 객체를 만들 때마다 매번 프로퍼티와 메소드도 새로 생성하기 때문에 메모리를 많이 차지한다.



##### 1-2) Functional Shared Instantiation

```javascript
var Animal = function(species, name) {
    var obj = {};
    obj.species = species;
    obj.name = name;
    //extend(obj, objMethods);
    return obj;
}
var extend = function(obj, methods) {
    for (var key in methods) {
        obj[key] = methods[key]
    }
}
var objMethods = {
    makeSound: function() {
        
    };
    eat: function() {
    };
	sleep: function() {
    
	};
}
```

- 필요한 메소드들을 객체를 생성하는 함수(=아래 예시 Animai 함수) 외부에서 독립적인 객체(=아래 예시 objMethods)로 정의한다. 객체를 생성하는 함수 내부에서 외부 함수의 메소드들을 수동으로 할당해준다 .
- 객체를 생성하는 일반 함수를 사용해 새로운 객체를 만들 때마다 매번 프로퍼티와 메소드를 새로 생성할 필요가 없다. 
- 단점 :  객체를 '만드는 시점’에 외부에 정의한 프로퍼티/메소드들을 가져오기 때문에, 만일 외부의 정의한 객체의 프로퍼티/메소드가 변경되어도, 변경 전에 해당 객체 생성 함수를 활용해 만들어진 새로운 객체에는 변경사항이 반영되지 않는다. 
  - 프로토타입이 이를 보완한다. 프로토타입은 '호출한 시점'의 메소드를 가져오기 때문에 변경사항이 반영된다.



### 2. 특정한 함수 생성자를 활용해 만든다. (생성자 패턴)

```javascript
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function() {
        alert(this.name);
    }
}

var person1 = new Person("Nicholas", 29, "Software Engineer");
var person2 = new Person("Greg", 27, "Doctor");

Person("A", 30, 20)
```

- 위의 일반 객체 생성 함수와 달리 1) 명시적으로 객체 생성를 생성하지 않으며 2) 프로퍼티와 메서드는 this객체에 직접적으로 할당되고 3) return문이 없다.
- 생성자 패턴의 함수를 활용해 새 객체(= 인스턴스)를 만들 때는 new 연산자를 사용해야한다. new 연산자를 사용해 생성자를 호출하면 내부적으로 다음과 같은 과정이 이루어진다. new 연산자를 사용하지 않는다면 this는 window에 바인딩되어 생성자 내의 프로퍼티들이 전역 스코프에 내에서 변수 할당이 된다. 
  1. 빈 객체를 생성한다.
  2. 생성자의 this 값에 새 객체를 할당한다. 따라서 this는 새 객체를 가리킨다.
  3. 생성자 내부 코드 실행한다. (= this로 참조되는 객체에 프로퍼티가 추가된다.) 
  4. 마지막에 다른 객체가 명시적으로 반환되지 않을 경우, this로 참조된 이 객체를 반환한다. 

- 변수의 첫글자를 대문자로 만들어 생성자 함수임을 명시한다.

- 네이티브 생성자로 Object와 Array가 있다. 

- 가장 큰 장점은 해당 생성자를 활용해 만들어진 객체가 '어떤 타입인지 알 수 있다'는 점이다. 

  ~~~javascript
  person1.constructor == Person // true
  person1 instanceof Person // true
  ~~~

- 생성자로 새 객체(= 인스턴스)를 만들 때 마다 메서드가 생성된다. 위 예시와 같이 만들면 인스턴스가 모두  sayName()이라는 메서드를 가지고 있더라도 이름만 같을 뿐 다르다. 이렇게 하지 않으려면 Functional Shared Instantiation(1-2 참조) 방식으로 메서드들을 생성자 밖으로 내보내면 된다.

  ~~~javascript
  function Person(name, age, job) {
      this.name = name;
      this.age = age;
      this.job = job;
      this.sayName = sayName;// 단순히 외부의 함수를 가리키는 포인터일 뿐.
  }
  
  function sayName() {
      alert(this.name);
  }
  
  // 하지만 일부 객체에서만 쓰이는 함수를 전역에 놓음으로써 전역 스코프를 어지럽힌다.
  ~~~



### 3. 함수의 prototype 프로퍼티를 활용해 만든다. (프로토타입 패턴 / Prototypal Instantiation)

```javascript
// 함수
function Person() {
}

// 함수 Person의 프로토타입 프로퍼티에 프로퍼티를 지정
Person.prototype.name = “Nicholas”
Person.prototype.age = 29;
Person.prototype.job = “Software Engineer”;
Person.prototype.sayName = function() {
 alert(this.name);
};

var person1 = new Person();
person1.sayName(); // “Nicholas”

var person2 = new Person();
person2.sayName(); // “Nicholas”

alert(person1.sayName == person2.sayName); // true
```

- 생성자 함수가 비어있어도 new 연산자를 사용해 생성자를 호출해 만든 객체에는 프로퍼티와 메서드가 존재한다. 생성자 패턴과는 달리 프로퍼티와 메서드를 모든 인스턴스에서 공유한다. 

- 모든 함수는 생성될 때마다 동일한 이름의 객체가 생기고, 이는 prototype프로퍼티를 가진다. 이 prototype 프로퍼티 역시 특정 규칙에 따라 생성된다. 

  - 함수의 모든 prototype 프로퍼티는 자동으로 constructor 프로퍼티를 갖는다. prototype의 다른 메서드는 Object에서 상속한다. prototype.constructor 프로퍼티는 해당 프로토타입이 프로퍼티로서 소속된 함수를 가리킨다. 

    ~~~javascript
    // 함수를 생성한다.
    function Person() {
    }
    
    // 생성된 함수는 객체이고, 이 객체는 prototype라는 이름의 프로퍼티를 갖고, 이 프로퍼티의 값은 constructor라는 프로퍼티를 가진 객체다.
    Person.prototype // {constructor: f}
    
    // prototype안의 constructor 프로퍼티 값은 생성자다. 
    Person.prototype.constructor // Person
    ~~~

- 생성자를 호출해서 인스턴스를 생성할 때마다 해당 인스턴스 내부에는 생성자의 프로토타입을 가리키는 포인터가 생성된다. 이 포인터를 [[prototype]] 이라 부르며, 파폭, 사파리, 크롬은 모두 _ _proto__라는 프로퍼티를 지원해 [[prototype]]에 접근할 수 있게한다. 이 프로퍼티는 해당 참조 타입의 인스턴스가 가져야 할 프로퍼티와 메서드를 담고 있다.

- 아래와 같이 외부 객체를 prototype으로 직접 할당하는 방법도 있다.

  ```javascript
  var Animal = function(species, name) {
      var obj = Object.create(objMethods); 
      // 함수 안에 외부 객체를 상속받은 객체 obj를 만든다.
      // Object.create는 객체를 만드는 프로퍼티로, 그 객체의 prototyped르 특정 객체로 설정한다.
      obj.species = species; // 필요한 프로퍼티는 수동으로 할당한다.
      obj.name = name;
      return obj;
  }
  var objMethods = {
      makeSound: function() {
      };
      eat: function() {
      };
  	sleep: function() {
  	};
  }
  ```

- 생성자 이름과 동일한 이름의 객체의 프로퍼티인 prototype의 프로퍼티와 메서드는 객체 인스턴스 전체에서 공유된다. 이는 장점이나 만일 값이 object나 array 처럼 참조타입이라면 문제가 될 수 있다. 

  ~~~javascript
  function Person() {
  }
  
  Person.prototype = {
      constructor: Person,
      name: "Nicholas",
      friends : ["Shelby", "Court"] // prototype 프로퍼티 중 하나 값이 참조타입이다. 
  }
  
  var person1 = new Person();
  var person2 = new Person();
  
  person1.friends.push("Van");
  
  person1.friends // ["Shelby", "Court", "Van"]
  person2.friends //  ["Shelby", "Court", "Van"] --> person2의 프로퍼티는 건들지 않았으나 값이 바뀌었다. 
  ~~~



#### 프로토타입과 in 연산자 (prototype과 instance의 프로퍼티 구분하는 법)

- in 연산자는 주어진 이름의 프로퍼티를 객체에서 접근할 수 있을 때 true를 반환한다. 즉 해당 프로퍼티가 인스턴스에 존재하든 프로토타입에 존재하든 모두 true를 반환한다.

- hasOwnProperty()는 프로퍼티가 인스턴스에 존재할 때만 true를 반환한다. 

- 아래와 같이 해당 프로퍼티가 프로토타입에서 온 건지 확인할 수 있다. 프로토타입에 해당 프로퍼티가 있더라도 인스턴스에서 덮어써서 가리고 있다면  false 반환

  ~~~javascript
  function hasPrototypeProperty(object, name) {
      return !Object.hasOwnProperty(name) && (name in object);
  }
  
  function() {
  }
  
  Person.prototype.name = "Nicholas"
  Person.prototype.age = 29;
  Person.prototype.job = "Software Engineer"
  Person.prototype.sayName = function() {
      alert(this.name);
  }
  
  var person = new Person();
  hasPrototypeProperty(person, "name") // true
  
  person.name = "Greg" // prototype에 있던 프로퍼티를 instance의 프로퍼티로 가렸다.
  hasPrototypeProperty(person, "name") // false
  ~~~

- For-in 루프는 [[enumerable]]이 false인 프로퍼티만 반환하는데, 여기에는 인스턴스 프로퍼티와 프로토타입 프로퍼티가 모두 포함되어있다. 개발자가 직접 지정한 프로퍼티는 항상 나열 가능하다.



#### 프로토타입과 대체 문법

- Person.prototype을 하나하나 써서 지정하지 말고 다음과 같이 캡슐화해서 지정할 수도 있다.

  ~~~javascript
  function Person() {
  }
  Person.prototype = {
      name: "Nicholas",
      age : 29,
      job : "Software Engineer",
      sayName : function() {
          alert(this.name);
      }
  };
  ~~~

  - Person.prototytpe 프로퍼티에 객체 리터럴로 생성한 객체를 덮어썼다.

  - 덮어쓰이기 전에는 Person.prototype.constructor = Person이었는데 사라졌으니, 이것도 수동으로 지정해주면 된다. 근데 이런 식으로 constructor를 재설정하면 프로퍼티의 enumerable 속성도 true된다. 고로 constructor도 아래와 같이 설정해줘야한다.

    ~~~javascript
    Object.defineProperty(Person.prototype, "constructor", {
         enumerable: false,
         value: Person
     })
    ~~~

     



### 4. 여러 패턴을 조합해서 만든다.



#### 생성자 패턴 + 프로토타입의 조합 (= Pseudoclassical Instantiation)

~~~javascript
var Animal = function(species, name) {
    this.species = species;
    this.name = name;
}

Animal.prototype.makeSound = function() {
},
Animal.prototype.makeSound = function() {
},
Animal.prototype.makeSound = function() {
},
~~~

~~~javascript
function Person(name, age, job) {
    this.name = name;
    this.age = age;
    this.job = job;
    this.friends = ["Shelby", "Court"];
}

Person.prototype = {
    constructor: Person,
    sayName : function() {
        alert(this.name);
    }
}

var person1 = new Person("Nicholas", 29, "Software Engineer");
var person2 = new Person("Greg", 27, "Doctor");

person1.friends.push("Van");
person1.friends // ["Shelby", "Court", "Van"]
person2.friends // ["Shelby", "Court"] ---> person1에 새 값을 push했어도 영향 없다.
person1.friends === person2.friends // false
person1.sayName === person2.sayName // true
~~~



### 동적 프로토타입 패턴



### 기생 생성자 패턴



### 방탄 생성자 패턴

