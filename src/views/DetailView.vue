<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1><a href="/">Movie Site</a></h1>
            </div>
        </div>
    </header>
    <main id="main">
        <DetailIntro v-if="movieBasic" :movie="movieBasic" />
        <DetailInfo v-if="movieInfo" :movie="movieInfo" />
        <DetailVideo v-if="movieVideo" :movie="movieVideo" />
        <DetailCredits v-if="movieCredits" :movie="movieCredits" />
    </main>
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailCredits from "../components/detail/DetailCredits.vue";
import DetailInfo from "../components/detail/DetailInfo.vue";
import DetailVideo from "../components/detail/DetailVideo.vue";

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailCredits,
        DetailInfo,
        DetailVideo
    },

    setup() {
        const movieBasic = ref(null);
        const movieCredits = ref(null);
        const movieInfo = ref(null);
        const movieVideo = ref(null);

        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                movieBasic.value = resMovieBasic.data;

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`)
                movieCredits.value = resMovieCredits;
                console.log(resMovieCredits);

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;

                const resMovieVideo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/videos?api_key=${apiKey}`)
                movieVideo.value = resMovieVideo.data;

            } catch (err) {
                console.log(err);
            }
        });

        return { movieBasic, movieCredits, movieInfo, movieVideo }
    }
}
</script>
