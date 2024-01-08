# TMDBapi로 영화사이트 만들기
TMDBapi를 활용해 Vue.js로 영화 사이트를 제작했습니다.   

<img src="src/assets/img/TMDBsite.JPG" alt="커버사진">   

이 사이트에서는 최신 영화, 인기 영화, 최고 평점 등 필터링 기능과   
영화의 줄거리나 동영상, 캐스터 등 상세 정보를 볼 수 있습니다.

## Vue.js 사용
Vue.js는 사용자 인터페이스를 만들기 위한 진보적인 프론트엔드 프레임워크입니다.   
웹 애플리케이션의 UI를 만들기 위해 사용되며, 다른 프레임워크 및 라이브러리와 결합하여 사용할 수 있는 유연하고 가벼운 특징을 갖추고 있습니다.

## 작업순서

```js
Vue.js - The Progressive JavaScript Framework

√ Project name: ... .
√ Package name: ... movie
√ Add TypeScript? ... No
√ Add JSX Support? ... Yes
√ Add Vue Router for Single Page Application development? ... Yes
√ Add Pinia for state management? ... No
√ Add Vitest for Unit Testing? ... No
√ Add an End-to-End Testing Solution? » No
√ Add ESLint for code quality? ... Yes
√ Add Prettier for code formatting? ... Yes

Scaffolding project in C:\Users\line\Documents\GitHub\movie-project2023...

Done. Now run:

  npm install
  npm run format
  npm run dev
```

## 사용 기술
- `onMounted` 훅 사용   
`onMounted` 훅은 Vue 3의 Composition API에서 제공되는 훅 중 하나입니다. 이 훅은 Vue 컴포넌트가 마운트된 후에 실행되는 동작을 정의할 수 있게 해줍니다. React의   
`useState` 훅과 같은 역할을 합니다.

- `<script setup>` 구문   
Vue 3에서 소개된 `<script setup>` 구문은 단일 파일 컴포넌트(Single File Components)에서 스크립트 부분을 간결하게 작성하는 방법 중 하나입니다. 이 구문은 `<script>` 태그를 대체하고, Composition API를 사용하여 코드를 더 간결하게 작성할 수 있도록 지원합니다.

- `axios` 사용   
`Axios`는 간단하고 직관적인 API를 제공하여 HTTP 요청을 보내고 응답을 받아올 수 있으며, JSON 데이터를 자동으로 변환해줍니다. 또한, 요청 취소, 요청/응답 인터셉터 등 다양한 기능을 제공하여 편리하게 HTTP 통신을 처리할 수 있습니다.

- `.env` 파일 
.evn파일에 VITE_API_KEY를 환경 변수로 설정하여 API키를 보호합니다.    불러올때는 `import.meta.env.VITE_API_KEY`로 불러옵니다.

- `try catch` 구문   
`try catch` 구문은 JavaScript에서 예외(에러)를 처리하기 위한 구문입니다.   
이 구문을 사용하는 이유는 예외가 발생했을 때 프로그램이 종료되거나 예기치 못한 동작을 하지 않도록 안전하게 예외를 처리하기 위함입니다.   
일반적으로 예상할 수 있는 에러 조건에 대해 미리 예외 처리를 하여 프로그램이 계속해서 실행될 수 있도록 보장합니다.


## 트러블슈팅
<details>
    <summary>비동기 호출 순서 오류</summary>   

    - 문제 원인   

        onMounted(() => {   
            ...{파라미터의 변수들}   
            try {
                const resMovieBasic = axios.get(`데이터를 불러올 주소`)   
                movieBasic.value = resMovieBasic.data;
            } catch (err) {
                console.log(err);
            }
        });

        `axios.get` 함수는 비동기적으로 실행되는데, onMounted 훅이 비동기 함수가   
        아닌 콜백 형태의  함수를 필요로 하기 때문에 `async await`를 사용해야한다.

    - 문제 해결 
    
        onMounted(async () => {
            try {
                const resMovieBasic = await axios.get(`데이터를 불러올 주소`)
                movieBasic.value = resMovieBasic.data;
            } catch (err) {
                console.log(err);
            }
        });

        이렇게 수정하면 비동기관련 문제가 해결된다.

</details>

## 스택
<div disflay="flex" flex-direction:column; align-items:flex-start;>
  <p><strong>Environment</strong></p>
  <div>
    <img src="https://img.shields.io/badge/VisualStudioCode-007ACC?style=flat-square&logo=VisualStudioCode&logoColor=white">
    <img src="https://img.shields.io/badge/Github-181717?style=flat-square&logo=Github&logoColor=white"> 
    <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=Git&logoColor=white">
  </div>
  <p><strong>Development</strong></p>
  <div>
    <img src="https://img.shields.io/badge/html5-E34F26?style=flat-square&logo=html5&logoColor=white"> 
    <img src="https://img.shields.io/badge/css-1572B6?style=flat-square&logo=css3&logoColor=white">
    <img src="https://img.shields.io/badge/javascript-F7DF1E?style=flat-square&logo=javascript&logoColor=white">
    <img src="https://img.shields.io/badge/Vue.js-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white">
  </div>