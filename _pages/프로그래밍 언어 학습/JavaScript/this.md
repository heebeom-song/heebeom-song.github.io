---
title: "this"
tags:
    - JavaScript
    - ProgrammingLanguage
    - NodeJs
date: "2025-04-08"
thumbnail: "/assets/img/thumbnail/js.png"
---

앞선 포스팅에 1. 스코프에 대해 정리했습니다.

다음으로 3. this에 대해 정리하겠습니다!

2.호출 스택을 먼저 정리하지 않는 이유는 4. 실행 컨텍스트와 2. 호출 스택은 아주아주아주아주 밀접하게 관련되어 있기때문에 함께 정리하여 포스팅하겠습니다!  
많관부 많관부!

# 22. this

## 22.1. this 키워드

this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수임.  
this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있음.  
this는 JS 엔진에 의해 암묵적으로 생성됨.  
코드 어디서든 참조 가능함.  
this 바인딩은 함수 호출 방식에 의해 동적으로 결정됨.  
객체 리터럴의 메서드 내부에서의 this는 메서드를 호출한 객체임.  
생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킴.  
전역에서 this는 전역 객체 window를 가리킴.  
strict mode가 적용된 일반 함수 내부의  this에는 undefined가 바인딩됨. -> 일반 함수 내부에서 this는 전역 객체 window를 가리키기 때문에 쓸모가 없음!

## 22.2. 함수 호출 방식과 this 바인딩

### 22.2.1. 일반 함수 호출

전역 함수는 물론이고 일반 함수로 호출된 모든 함수(중첩 함수, 콜백 함수 포함) 내부의 this에는 전역 객체가 바인딩됨.  
이는 외부 함수인 메서드와 중첩 함수 또는 콜백 함수의 this가 일치하지 않는다는 것을 뜻하고 이렇게 되면 중첩 함수 또는 콜백 함수를 헬퍼 함수로 동작하기 어렵게 만듦.  
이를 해결하기 위해 아래 3가지 방법이 주로 쓰임.

1. this 바인딩을 변수(that 등)에 할당함.

```js
const obj = {
    value: 100,
    foo() {
        const that = this;

        setTimeout(function(){
            console.log(that.value);
        }, 100);
    }
};
```

2. Function.prototype.bind() 메서드 사용.

```js
const obj = {
    value: 100,
    foo() {
        setTimeout(function(){
            console.log(this.value);
        }.bind(this), 100);
    }
};
```

3. 화살표 함수 사용 (화살표 함수의 함수 내부 this는 상위 스코프의 this를 가리킴.)

```js
const obj = {
    value: 100,
    foo() {
        setTimeout(()=> console.log(this.value), 100);
    }
};
```

### 22.2.2. 메서드 호출

메서드 내부의 this에는 메서드를 호출한 객체가 바인딩됨.  
프로토타입 메서드 내부에서 사용된 this도 일반 메서드와 마찬가지로 해당 메서드를 호출한 객체에 바인딩됨.

### 22.2.3. 생성자 함수 호출

생성자 함수 내부의 this에는 생성자 함수가 생성할 인스턴스 바인딩됨.

### 22.2.4. Function.prototype.apply/call/bind 메서드에 의한 간접 호출

Function.prototype의 메서드들임.  
apply와 call 메서드는 호출할 함수에 인수를 전달하는 방식만 다를 뿐 this로 사용할 객체를 전달하면서 함수를 호출하는 것은 동일함.  
apply와 call 메서드의 대표적인 용도는 유사 배열 객체와 같은 배열이 아닌 객체가 Array.prototype.slice 같은 배열 메서드를 사용할 수 있게 해줌.

```js
const arr = Array.prototype.slice.call(arguments);
```

bind 메서드는 첫 번째 인수로 전달한 값으로 this 바인딩이 교체된 함수를 새롭게 생성하여 반환함.

```js
const person = {
    name: 'Lee',
    foo(callback){
        setTimeout(callback.bind(this), 100);
    }
};
```

함수 호출 방식에 따른 this 동적 바인딩은 아래와 같음!

|함수 호출 방식|this 바인딩|
|-------------|----------|
|일반 함수 호출|전역 객체|
|메서드 호출|메서드를 호출한 객체|
|생성자 함수 호출|생성자 함수가 생성할 인스턴스|
|Function.prototype.apply/call/bind 메서드에 의한 간접 호출|Function.prototype.apply/call/bind 메서드에 첫 번째 인수로 전달한 객체|

이상 this에 대해 정리해 보았습니다!  
스코프 포스팅과 마찬가지로 이웅모님의 모던 자바스크립트 Deep Dive를 참고했습니다.

-end-