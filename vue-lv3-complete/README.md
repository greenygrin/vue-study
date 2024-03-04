# Vue.js 완벽 가이드 - 실습과 리팩토링으로 배우는 실전 개념

1. Vue.js 를 이용한 **웹 서비스 구현 절차**
2. 실무 프로젝트 진행 방식 (컴포넌트, **라우터, API, 스토어**)
3. **컴포넌트 디자인 패턴**과 **자바스크립트 비동기 처리**
4. **Mixins**과 **HOC**를 이용한 컴포넌트 재활용 방법
5. **외부 라이브러리 모듈화** 및 **실무 프로젝트 구성** 방법
6. 사용자 경험을 높이는 라우터 설계 방법과 **고급 라우터 패턴**

> [Vue.js 공식 문서](https://vuejs.org/)
>
> [캡틴판교의 Cracking Vue.js](https://joshua1988.github.io/vue-camp/)
>
> [제작할 사이트 - 해커 뉴스](https://news.ycombinator.com/)
>
> [해커 뉴스 API 문서 주소](https://github.com/tastejs/hacker-news-pwas/blob/master/docs/api.md)



## 깃헙 리포지토리 클론

> [Vue.js 실전 강좌 리포지토리](https://github.com/joshua1988/vue-advanced)

```shell
git clone https://github.com/joshua1988/vue-advanced.git
```


## Todo App 프로젝트 생성

```shell
vue create vue-news
cd vue-todo
npm run serve
```

## Vue CLI 3.x에서 ESLint 설정 끄는 방법

프로젝트 폴더 내 vue.config.js 파일 생성

```shell
    module.exports = {
        lintOnSave: false
    }
```

## 라우터 설치 및 구현

```shell
npm i vue-router --save
```

./src/routes/index.js
./src/views/x.vue

./src/main.js 에 라우터 연결


## API 구현

Axios 설치

```shell
npm i axios --save
```

./scr/api/index.js


## 자바스크립트 비동기 처리

- Callback
  > [비동기 처리와 콜백 함수](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)

- Promise
  > [자바스크립트 Promise 쉽게 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)


## 스토어 구현

Vuex는 상태 관리 도구. 상태라는 것은 여러 컴포넌트 간의 공유되는 데이터 속성.

Vuex 설치

```shell
npm i vuex
```

./scr/store/index.js


### Vuex 사용 전 vs 후

API ----> NewsView

API ----> Vuex (actions > mutations > state) ----> NewsView


## 라우터

> [v-html API 문서](https://vuejs.org/v2/api/#v-html)
>
> [v-html과 데이터 바인딩 차이점 문서](https://vuejs.org/v2/guide/syntax.html#Raw-HTML)
>
> [라우터 트랜지션 문서](https://vuejs.org/v2/guide/transitions.html)
>
> [뷰 트랜지션 문서](https://router.vuejs.org/guide/advanced/transitions.html#per-route-transition)


## 데이터 호출 시점

1. 라우터 네이게이션 가드
    - 특정 URL로 접근하기 전의 동작을 정의하는 속성(함수)

> [네비게이션 가드 블로그 글](https://joshua1988.github.io/web-development/vuejs/vue-router-navigation-guards/)
>
> [네비게이션 가드 뷰 라우터 공식 문서](https://router.vuejs.org/guide/advanced/navigation-guards.html#global-guards)

2. 컴포넌트 라이프 사이클 훅
   - created : **컴포넌트가 생성**되자마자 호출되는 로직

> [created 라이프 사이클 훅 API 문서](https://vuejs.org/v2/api/#created)


## 컴포넌트 디자인 패턴

1. Common - 기본적인 컴포넌트 등록과 컴포넌트 통신
2. Slot - 마크업 확장이 가능한 컴포넌트
3. Controlled - 결합력이 높은 컴포넌트
4. Renderless - 데이터 처리 컴포넌트