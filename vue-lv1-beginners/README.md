# Vue.js 시작하기 - Age of Vue.js
- Reactivity
- 인스턴스
- 컴포넌트
- 컴포넌트 통신
    - props
    - event emit
- HTTP 통신 라이브러리 (axios)
- 템플릿 문법
    - 데이터 바인딩
    - 뷰 디렉티브 (v-)
- Vue CLI
- 싱글 파일 컴포넌트


## 사전 참고

> [Vue.js 공식 문서](https://vuejs.org/)
>
> [캡틴판교의 Cracking Vue.js](https://joshua1988.github.io/vue-camp/)
> : 기본적인 자바스크립트 개념부터 Vue.js 기본, 실무 지식까지 모두 정리
>
> [수업 소스 코드 - 깃헙 리퍼지토리](https://github.com/joshua1988/learn-vue-js)


## 개발 환경 설정
Chrome, VSCode, Node.js, Vue.js Devtools 설치

> [Node.js](https://nodejs.org/en/)
>
> [Vue.js Devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)

-----------------------------

## 강의 참고

### Vue.js 소개 - Reactivity
> [Object.defineProperty() API 문서](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)
>
> [즉시 실행 함수 MDN 문서](https://developer.mozilla.org/ko/docs/Glossary/IIFE)


### 인스턴스

인스턴스의 속성, API들

```js
new Vue({
    el: ,
    template: ,
    data: ,
    methods: ,
    created: ,
    watch: ,
});
```

- el : 인스턴스가 그려지는 화면의 시작점 (특정 HTML 태그)
- template : 화면에 표시할 요소 (HTML, CSS 등)
- data : 뷰의 반응성(Reactivity)이 반영된 데이터 속성
- methods : 화면의 동작과 이벤트 로직을 제어하는 메서드
- created : 뷰의 라이프 사이클과 관련된 속성
- watch : data에서 정의한 속성이 변화했을 때 추가 동작을 수행할 수 있게 정의하는 속성

> [MDN 생성자 함수 설명 문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Obsolete_Pages/Core_JavaScript_1.5_Guide/Creating_New_Objects/Using_a_Constructor_Function)
>
> [MDN Prototype 설명 문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor)


### 컴포넌트
> [this 관련 글1](https://www.w3schools.com/js/js_this.asp)
>
> [this 관련 글2](https://medium.com/better-programming/understanding-the-this-keyword-in-javascript-cb76d4c7c5e8)


### 라우터
> [라우터 공식 사이트 설치 문서](https://router.vuejs.org/installation.html)
>
> [네비게이션 가드 블로그 글](https://joshua1988.github.io/web-development/vuejs/vue-router-navigation-guards)


### HTTP 통신 라이브러리 - axios
> [Ajax 위키백과](https://ko.wikipedia.org/wiki/Ajax)
>
> [Vue Resource 깃헙 주소](https://github.com/pagekit/vue-resource)
>
> [Axios 깃헙 주소](https://github.com/axios/axios)
>
> [jsonplaceholder 사이트](https://jsonplaceholder.typicode.com/)
>
> [자바스크립트 동작 원리](https://joshua1988.github.io/web-development/translation/javascript/how-js-works-inside-engine/)


### 자바스크립트의 비동기 처리 패턴
1. callback
2. promise
3. promise + generator
4. async & await

> [자바스크립트 비동기 처리와 콜백 함수](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)
>
> [자바스크립트 Promise 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
>
> [자바스크립트 async와 await]()https://joshua1988.github.io/web-development/javascript/js-async-await/


### 크롬 개발자 도구 네티워크 패널 보는 방법
> [프런트엔드 개발자가 알아야 하는 HTTP 프로토콜](https://joshua1988.github.io/web-development/http-part1/)
>
> [구글 크롬 개발자 도구 공식 문서](https://developers.google.com/web/tools/chrome-devtools/)


### 템플릿 문법


> [Form Input Binding 공식 문서](https://vuejs.org/v2/guide/forms.html#ad)
>
> [watch 속성과 computed 속성 차이점에 관한 공식 문서](https://vuejs.org/v2/guide/computed.html#ad)
>
> [참고](https://joshua1988.github.io/vue-camp/vue/template.html)


### 프로젝트 생성 도구 - Vue CLI

> [Vue CLI 공식 사이트 링크](https://cli.vuejs.org/)


1. 버전확인
```shell
node -v (10 이상)
npm -v (6 이상)
```

2. 설치
npm install -g @vue/cli

3. 에러 시
sudo npm install -g @vue/cli


#### 프로젝트 생성

- Vue CLI 3.x
```shell
vue create '프로젝트 폴더 위치'
```

- Vue CLI 4.5.x 이상
```shell
Default ( [Vue 2] bable, eslint ) 선택
```
> [리눅스 기본 명령어](https://joshua1988.github.io/web-development/linux-commands-for-beginners/)

- 실습
```shell
vue create vue-cli
cd vue-cli
npm run serve
```

#### 서버 종료
<kbd>ctrl</kbd> + <kbd>c</kbd>

#### x.vue 파일 자동완성
vu 입력 후 <kbd>tab</kbd> 클릭

#### axios 설치
```shell
npm i axios
```

```js
<script>
    import axios from 'axios';
</script>
```

-----------------------------

## 향후 학습 방향
- 공식 문서 정독 추천 (번역본보다 원문으로 보는 것 추천)
    - Learn > Guide, API, Style Guide, Cookbook