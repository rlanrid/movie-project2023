<script setup>
// import { ref, onMounted } from 'vue';
// import axios from 'axios';

// const movies = ref([]);
// const searchTerm = ref('');

// const fetchMovies = async (category) => {
//   let url = 'https://api.themoviedb.org/3/movie/popular'
//   switch (category) {
//     case 'latest':
//       url = 'https://api.themoviedb.org/3/movie/now_playing';
//       break;
//     case 'popular':
//       url = 'https://api.themoviedb.org/3/movie/popular';
//       break;
//     case 'upcoming':
//       url = 'https://api.themoviedb.org/3/movie/upcoming';
//       break;
//     case 'toprated':
//       url = 'https://api.themoviedb.org/3/movie/top_rated';
//       break;
//   }

//   try {
//     const response = await axios.get(url, {
//       params: {
//         api_key: '39fda1c069a36899bfba2521758ec9c6',
//         language: 'ko-KR',
//         page: '1'
//       }
//     });
//     console.log(response);
//     movies.value = response.data.results;
//     console.log(movies);
//   } catch (err) {
//     console.log(err)
//   }
// }

// const searchMovies = async () => {
//   try {
//     const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
//       params: {
//         api_key: '39fda1c069a36899bfba2521758ec9c6',
//         language: 'ko-KR',
//         query: searchTerm.value,
//         page: '1'
//       }
//     });
//     console.log(response);
//     movies.value = response.data.results;
//   } catch (err) {
//     console.log(err)
//   }
// }

// onMounted(async () => {
//   await fetchMovies('latest');
// });
</script>

<template>
  <HeaderSection />

  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        <MovieSearch @onSearch="search" />
        <MovieTag @onSearch="tags" />
        <MovieCont />
      </div>
    </div>
  </main>
  <FooterSection />
</template>

<script>
import HeaderSection from '@/components/section/HeaderSection.vue'
import FooterSection from '@/components/section/FooterSection.vue'

import MovieSearch from '@/components/contents/MovieSearch.vue';
import MovieTag from '@/components/contents/MovieTag.vue';
import MovieCont from '@/components/contents/MovieCont.vue';

export default {
  name: "Movie Home Page",
  components: {
    HeaderSection,
    FooterSection,
    MovieSearch,
    MovieTag,
    MovieCont
  },
  data() {
    return {
      movies: [],
    }
  },
  methods: {
    async search(query) {
      try {
        const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=39fda1c069a36899bfba2521758ec9c6&language=ko-KR&query=${query}`);
        const result = await response.json();
        console.log(result);
      } catch (error) {
        console.log(error)
      }
    },
    async tags(query) {
      try {
        const response = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=39fda1c069a36899bfba2521758ec9c6&language=ko-KR&query=${query}`);
        const result = await response.json();
        console.log(result);
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style lang="scss">
.movie__search {
  margin: 50px 0 20px 0;
  position: relative;

  input {
    border: 1px solid var(--black500);
    padding: 1rem 2rem;
    width: 100%;
    border-radius: 50px;
  }

  button {
    position: absolute;
    right: 6px;
    top: 6px;
    width: 40px;
    height: 40px;
    background-color: var(--black);
    color: var(--white);
    border-radius: 50%;
    cursor: pointer;
  }
}

.movie__tag {

  ul {
    display: flex;

    li {
      a {
        border: 1px solid var(--black);
        padding: 0.5rem 1.3rem;
        display: inline-block;
        border-radius: 50px;
        margin: 20px 10px 20px 0;
        transition: all 0.3s;

        &:hover {
          background-color: var(--black);
          color: var(--white);
        }
      }
    }
  }
}

.movie__cont {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  .movie {
    width: 24%;
    margin-bottom: 1.5%;
    background-color: #ccc;

    img {
      height: 100%;
    }
  }
}
</style>
