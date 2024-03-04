# Vue.js 중급 강좌 - 웹앱 제작으로 배워보는 Vue.js, ES6, Vuex
1. 뷰 CLI를 이용한 **프로젝트 구성** 방법
2. **컴포넌트 기반 설계** 방법
3. **컴포넌트 구조화** 및 **컴포넌트 통신** 방법
4. **ES6**를 이용한 효율적이고 간결한 뷰 코딩 방법
5. **Vuex**를 이용한 상태 관리의 이해 및 적용 방법

## 사전 참고

> [Vue.js 공식 문서](https://vuejs.org/)
>
> [캡틴판교의 Cracking Vue.js](https://joshua1988.github.io/vue-camp/)
> : 기본적인 자바스크립트 개념부터 Vue.js 기본, 실무 지식까지 모두 정리


## 개발 환경 설정
Chrome, VSCode, Node.js, Vue.js Devtools, Git을 설치

> [Node.js](https://nodejs.org/en/)
>
> [Vue.js Devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
>
> [Git](https://git-scm.com/downloads)


## 깃 관련 학습 안내

> [초심자를 위한 Github 협업 튜토리얼](https://milooy.wordpress.com/2017/06/21/working-together-with-github-tutorial/)


## 깃헙 리포지토리 클론

> [vue-intermediate](https://github.com/joshua1988/vue-intermediate)

```shell
git clone https://github.com/joshua1988/vue-intermediate.git vue-intermediate
cd vue-intermediate
ls
git status
```

- 브랜치 이동 예시

```shell
git checkout es6/const-let
cd vue-todo/
ls -ll
```


## Todo App 프로젝트 생성

```shell
vue create vue-todo
cd vue-todo
npm run serve
```

## 깃헙 브랜치

```shell
git checkout todo-app/components-implementation
```

----------------------------

## ES6 for Vue.js

- ES6의 여러가지 문법 중 Vue.js 코딩을 간편하게 해주는 문법 학습
- const & let, Arrow Function, Enhanced Object Literals, Modules 학습

### ES6 란?

- ECMAScript 2015와 동일한 용어
- 2015년은 ES5(2009년)이래로 진행한 첫 메이저 업데이트가 승인된 해
- 최신 Front-End Framework인 React, Angular, Vue에서 권고하는 언어 형식
- ES5에 비해 문법이 간결해져서 익숙해지면 코딩을 훨씬 편하게 할 수 있음

### Babel

- 구 버전 브라우저 중에서 ES6의 기능을 지원하지 않는 브라우저가 있으므로 transpiling이 필요
- ES6의 문법을 각 브라우저의 호환 가능한 ES5로 변환하는 컴파일러
```js
module: {
    loader: [{
        test: /\.js$/,
        loader: 'babel-loader',
        query: {
            presets: ['es2015']
        }
    }]
}
```

### const & let - 새로운 변수 선언 방식

- 블록 단위 { } 로 변수의 범위가 제한되었음
- const : 한번 선언한 값에 대해서 변경할 수 없음 (상수 개념)
    * 하지만, 객체나 배열의 내부는 변경할 수 있다. ({}, [])
- let : 한번 선언한 값에 대해서 다시 선언할 수 없음


### Arrow Function - 화살표 함수

- 함수를 정의할 때 function 이라는 키워드를 사용하지 않고 => fh eocp
- 흔히 사용하는 **콜백 함수**의 문법을 간결화

```js
// ES5 함수 정의 방식
var sum = function(a, b) {
    return a + b;
};

// ES6 함수 정의 방식
var sum = (a, b) => {
    return a + b;
}

sum(10, 20);
```

```js
// ES5
var arr = ['a', 'b', 'c'];
arr.forEach(function(value) {
    console.log(value); // a, b, c
});

// ES6
var arr = ['a', 'b', 'c'];
arr.forEach(value => console.log(value)); //a, b, c
```


### Enhanced Object Literals - 향상된 객체 리터럴

- 객체의 속성을 메서드로 사용할 때 function 예약어를 생략하고 생성 가능

```js
var dictionary = {
    words: 100,
    // ES5
    lookup: function() {
        console.log('find words')l
    },
    // ES6
    lookup() {
        console.log('find words');
    }
}
```

- 객체의 속성명과 값 명이 동일할 때 아래와 같이 축약 가능

```js
var figures = 10;
var dictionary = {
    // figures: figures,
    figures
};
```


### Modules - 자바스크립트 모듈화 방법

- 자바스크립트 모듈 로더 라이브러리(AMD, Commons JS)기능을 js 언어 자체에서 지원
- 호출되기 전까지는 코드 실행과 동작을 하지 않는 특징이 있음

```js
// libs/math.js
export function sum(x, y) {
    return x + y;
}
export var pi = 3.141593;

// main.js
import {sum} from 'libs/math.js';
sum(1, 2);
```

- Vue.js 에서 자주 마주칠 default export

```js
// utill.js
export default function (x) {
    return console.log(x);
}

// main.js
import util from 'util.js';
console.log(util);  // function (x) { return console.log(x); }
util('hi');

// app.js
import log from 'util.js';
console.log(log);
log('hi');
```

----------------------------

## Vuex - 상태 관리 라이브러리

- 복잡한 애플리케이션의 컴포넌트들을 효율적으로 관리하는 Vuex 라이브러리 소개
- Vuex 라이브러리의 등장 배경인 Flux 패턴 소개
- Vuex 라이브러리의 주요 속성인 state, getters, mutations, actions 학습
- Vuex를 더 쉽게 코딩할 수 있는 방법인 Helper 기능 소개
- Vuex로 프로젝트를 구조화하는 방법과 모듈 구조화 방법 소개


### Vuex란?

- 무수히 많은 컴포넌트의 데이터를 관리하기 위한 상태 관리 패턴이자 라이브러리
- React의 Flux 패턴에서 기인함
- Vue.js 중고급 개발자로 성장하기 위한 필수 관문


### Flux란?

- MVC 패턴의 복잡한 데이터 흐름 문제를 해결하는 개발 패턴 - Unidirectional data flow

Flux 패턴
[Action] → [Dispatcher] → [Model] → [View]

1. action : 화면에서 발생하는 이벤트 또는 사용자의 입력
2. dispatcher : 데이터를 변경하는 방법, 메서드
3. model : 화면에 표시할 데이터
4. view : 사용자에게 비춰지는 화면

MVC 패턴
[Controller] → [Model] ↔ [View]


### MVC 패턴의 문제점

- 기능 추가 및 변경에 따라 생기는 문제점을 예측할 수가 없음. (예) 페이스북 채팅 화면
- 앱이 복잡해지면서 생기는 업데이트 루프


### Flux 패턴의 단반향 데이터 흐름

- 데이터의 흐름을 여러 갈래로 나뉘지 않고 단반향으로만 처리

                --------  [Action] -----
                ↓                      |
[Action] → [Dispatcher] → [Model] → [View]


### Vuex가 왜 필요할까?

- 복잡한 애플리케이션에서 컴포넌트의 개수가 많아지면 컴포넌트 간에 데이터 전달이 어려워진다.

- Vuex로 해결할 수 있는 문제
1. MVC 패턴에서 발생하는 구조적 오류
2. 컴포넌트 간 데이터 전달 명시
3. 여러 개의 컴포넌트에서 같은 데이터를 업데이트 할 때 동기화 문제


### Vuex 컨셉

- State : 컴포넌트 간에 공유하는 데이터 **data()**
- View : 데이터를 표시하는 화면 **template**
- Action : 사용자의 입력에 따라 데이터를 변경하는 **methods**


### Vuex 구조

컴포넌트 → 비동기 로직 → 동기 로직 → 상태


### Vuex 설치

- Vuex는 싱글 파일 컴포넌트 체계에서 NPM 방식으로 라이브러리를 설치하는 게 좋다.

```shell
npm install vuex --save
```
※ ES6와 함께 사용해야 더 많은 기능과 이점을 제공받을 수 있음


### Vuex 시작하기

- scr 폴더 안에 store 폴더 만들고 index.js 파일 생성

```js
import Vue from 'vue'
import Vue from 'vuex'

Vue.use(Vuex);

export const store = new Vuex.Store({
    // ...
});
```


### Vuex 기술 요소

- state : 여러 컴포넌트에 공유되는 데이터 **data**
- getters : 연산된 state 값을 접근하는 속성 **computed**
- mutations : state 값을 변경하는 이벤트 로직·메서드 **methods**
- actions : 비동기 처리 로직을 선언하는 메세더 **aysnc methods**


### state란?

- 여러 컴포넌트 간에 공유할 데이터 - **상태**

```js
// Vue
data: {
    message: 'Hello Vue.js!'
}

// Vuex
state: {
    message: 'Hello Vue.js!'
}
```

```html
<!-- Vue -->
<p>{{ message }}</p>

<!-- Vuex -->
<p>{{ this.$store.state.message }}</p>
```


### gatters란?

- state 값을 접근하는 속성이자 computed() 처럼 미리 연산된 값을 접근하는 속성

```js
// store/index.js
state: {
    num: 10
},
gatters: {
    getNumber(state) {
        return state.num;
    },
    doubleNumber(state) {
        return state.num * 2;
    }
}
```

```html
<p>{{ this.$store.gatters.getNumber }}</p>
<p>{{ this.$store.gatters.doubleNumber }}</p>
```


### mutations란?

- state의 값을 변경할 수 있는 **유일한 방법**이자 메서드
- 뮤테이션은 **commit()**으로 동작시킨다.

```js
// store/index.js
state: { num: 10 },
mutations: {
    printNumber(state) {
        return state.num
    },
    sumNumbers(state, anotherNum) {
        return state.num + anotherNum;
    }
}

// App.vue
this.$store.commit('printNumbers');
this.$store.commit('sumNumbers', 20);
```


### mutations의 commit() 형식

- state를 변경하기 위해 mutations를 동작시킬 때 인자(payload)를 전달할 수 있음

```js
// store/index.js
state: { storeNum: 10 },
mutations: {
    modifyState(state, payload) {
        console.log(payload.str);
        return state.storeNum += paylaod.num;
    }
}

// App.vue
this.$store.commit('modifyState', {
    str: 'passed from payload',
    num: 20
});
```

### state는 왜 직접 변경하지 않고 mutations로 변경할까?

- 여러 개의 컴포넌트에서 아래와 같이 state 값을 변경하는 경우 **어느 컴포넌트에서 해당 state를 변경했는지 추척하기가 어렵다.**
```js
methods: {
    increaseCounter() { this.$store.state.counter++; }
}
```
- 특정 시점에 어떤 컴포넌트가 state를 접근하여 변경한 건지 확인하기 어렵기 때문
- 따라서, 뷰의 반응성을 거스르지 않게 명시적으로 상태 변화를  수행. **반응성, 디버깅, 테스팅 혜택**


### actions란?

- 비동기 처리 로직을 선언하는 메서드. 비동기 로직을 담당하는 mutations
- 데이터 요청, Promise, ES6 async과 같은 비동기 처리는 모두 actions에 선언

```js
// store/index.js
state: {
    num: 10
},
mutations: {
    doubleNumber(state) {
        state.num * 2;
    }
},
actions: {
    delayDoubleNumber(context) {  // context로 store의 메서드와 속성 접근
        context.commit('doubleNumber');
    }
}

// App.vue
this.$store.dispatch('delayDoubleNumber');
```

actions 비동기 코드 예제 1
```js
// store/index.js
mutations: {
    addCouter(state) {
        state.counter++;
    }
},
actions: {
    delayAddNumber(context) {
        setTimeout(() => context.commit('addCounter'), 2000);
    }
}

// App.vue
methods: {
    incrementCounter() {
        this.$store.dispatch('delayAddNumber');
    }
}
```

actions 비동기 코드 예제 2
```js
// store/index.js
mutations: {
    setData(state, fetchedData) {
        state.product = fetchedData;
    }
},
actions: {
    fetchProductData(context) {
        return axios.get('https://domain.com/product/1')
                    .then(response = > context.commit('setData', response));
    }
}

// App.vue
methods: {
    getProduct() {
        this.$store.dispatch('fetchProductData');
    }
}
```

> [Promise 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
>
> [자바스크립트 비동기 처리 이해하기](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)


### 왜 비동기 처리 로직은 actions에 선언해야 할까?

- 언제 어느 컴포넌트에서 해당 state를 호출하고, 변경했는지 확인하기가 어려움

> 여러 개의 컴포넌트에서 mutations로 시간 차를 두고 state를 변경하는 경우
> 결론 : state 값의 변화를 추척하기 어렵게 때문에 mutations 속성에는 동기 처리 로직만 넣어야 한다.


### 각 속성들을 더 쉽게 사용하는 방법 - Helper

Store에 있는 아래 4가지 속성들을 간편하게 코딩하는 방법
- state -> mapState
- getters -> mapGetters
- mutations -> mapMutations
- actions -> mapActions


### 헬퍼의 사용법

헬퍼를 사용하고자 하는 vue 파일에서 아래와 같이 해당 헬퍼를 로딩

```js
//App.vue
import { mapState } from 'vuex'
import { mapGetters } from 'vuex'
import { mapMutations } from 'vuex'
import { mapActions } from 'vuex'

export default {
    compute() { ...mapState(['num']), ...mapGetters(['countedNum']) },
    methods() { ...mapMutations(['clickBtn']), ...mapActions(['asyncClickBtn']) }
}
```

...는 ES6의 **Object Spread Operator** 입니다

```js
let josh = {
    field: 'web',
    language: 'js'
};

let developer = {
    nation: 'korea',
    // field: josh.field,
    // language: josh.language
    ...josh
}
```


### mapState

- Vuex에 선언한 state 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

```js
// App.vue
import { mapState } from 'vuex'

computed() {
    ...mapState(['num'])
    // num() { return this.$store.state.num }
}

// store/index.js
state: {
    num: 10
}
```

```html
<!-- <p>{{ this.$store.state.num }}</p> -->
<p>{{ this.num }}</p>
```


### mapGetters

- Vuex에 선언한 getters 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

```js
// App.vue
import { mapGatters } from 'vuex'

computed() { ...mapGatters(['reverseMessage']) }

// store/index.js
gatters: {
    reverseMessage(state) {
        return state.msg.slit('').reverse().join('');
    }
}
```

```html
<!-- <p>{{ this.$store.getters.reverseMessage }}</p> -->
<p>{{ this.reverseMessage }}</p>
```


### mapMutations

- Vuex에 선언한 mutations 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

```js
// App.vue
import { mapMutations } from 'vuex'

methods: {
    ...mapMutations(['clickBtn']),
    authLogin() {},
    displayTable() {}
}

// store/index.js
mutations: {
    clickBtn(state) {
        alert(state.msg);
    }
}
```

```html
<button @click="clickBtn">popup message</button>
```


### mapActions

- Vuex에 선언한 actions 속성을 뷰 컴포넌트에 더 쉽게 연결해주는 헬퍼

```js
// App.vue
import { maActions } from 'vuex'

methods: {
    ...maActions(['delayClickBtn']),
}

// store/index.js
actions: {
    delayClickBtn(context) {
        setTimeout(() => context.commit('clickBtn'), 2000);
    }
}
```

```html
<button @click="delayClickBtn">delay popup message</button>
```


### 헬퍼의 유연한 문법

- Vuex에 선언한 속성을 그대로 컴포넌트에 연결하는 문법

```js
// 배열 리터럴
...mapMutations([
    'clickBtn', // 'clickBtn': clickBtn
    'addNumber' // addNumber(인자)
]);
```

- Vuex에 선언한 속성을 컴포넌트의 특정 메서드에다가 연결하는 문법

```js
// 객체 리터럴
...mapMutation({
    popupMsg: 'clickBtn'  // 컴포넌트 메서드 명 : Store의 뮤테이션 명
})
```


### 프로젝트 구조화와 모듈화 방법1

아래와 같은 store 구조를 어떻게 모듈화 할 수 있을까?

```js
// store/index.js
import Vue from 'vue'
import Vuex from 'vuex'

export const store = new Vuex.store({
    state: {},
    gatters: {},
    mutations: {},
    actions: {}
});
```

힌트! Vuex.Store({}) 의 속성을 모듈로 연결

- ES6의 Import & Export를 이요하여 속성별로 모듈화

```js
import Vue from 'vue'
import Vuex from 'vuex'
import * as getters from 'store/getters.js'
import * as mutations from 'store/mutations.js'
import * as actions from 'store/actions.js'

export const store = new Vuex.store({
    state: {},
    gatters,
    mutations,
    actions
});
```


### 프로젝트 구조화와 모듈화 방법2

- 앱이 비대해져서 1개의 store로는 관리가 힘들 때 modules 속성 사용

```js
// store/index.js
import Vue from 'vue'
import Vuex from 'vuex'
import todo from 'modules/togo.js'

export const store = new Vuex.Store({
    modules: {
        moduleA: todo,  // 모듈 명칭 : 모듈 파일명
        todo    // todo: todo
    }
});

// togo.js
const state = {}
const getters = {}
const mutations = {}
const actions = {}
```