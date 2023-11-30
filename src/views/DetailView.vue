<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>Movie Site</h1>
                <nav>
                    <ul>
                        <li><a href="#">공포 영화 TOP10</a></li>
                        <li><a href="#">슬픈 영화 TOP10</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    <main id="main">
        <DetailIntro v-if="movieBasic" :movie="movieBasic" />
        <DetailCredits v-if="movieCredits" :movie="movieCredits" />
        <DetailReview v-if="movieReview" :movie="movieReview" />
        <!-- <DetailInfo v-if="movieInfo" :movie="movieInfo" /> -->
    </main>
</template>

<script>
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailCredits from "../components/detail/DetailCredits.vue";
// import DetailInfo from "../components/detail/DetailInfo.vue";
import DetailReview from "../components/detail/DetailReview.vue";

export default {
    name: "MovieDetailPage",

    components: {
        DetailIntro,
        DetailCredits,
        DetailReview
    },

    setup() {
        const movieBasic = ref(null);
        const movieCredits = ref(null);
        // const movieInfo = ref(null);
        const movieReview = ref(null);

        const route = useRoute();

        onMounted(async () => {
            const movieId = route.params.movieId;
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = "ko-KR";

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                movieBasic.value = resMovieBasic.data;
                console.log(resMovieBasic.data)

                const resMovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`)
                movieCredits.value = resMovieCredits;
                console.log(movieCredits.value.data.cast)

                // const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`)
                // movieInfo.value = resMovieInfo.data;
                // console.log(resMovieInfo.data)

                const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}/reviews?language=${language}&api_key=${apiKey}&page=1`, options)
                movieReview.value = resMovieReview.data;
                console.log(resMovieReview.data)

            } catch (err) {
                console.log(err);
            }
        });

        return { movieBasic, movieCredits, movieReview }
    }
}
</script>

<style lang="scss">
.detail__intro {
    .container {
        display: flex;
        justify-content: space-between;
        padding-top: 100px;
        position: relative;
        z-index: 10;

        .left {
            width: 350px;
        }

        .right {
            width: calc(100% - 350px);
            margin-left: 2%;
            display: flex;
            flex-direction: column;
            justify-content: space-between;

            h2 {
                font-size: 26px;
                margin-bottom: 10px;
            }

            p {
                font-size: 16px;
            }

            .desc {
                margin-bottom: 10px;
            }

            .credits {
                display: flex;
                align-items: center;

                div {
                    width: 150px;
                    margin-right: 15px;
                }
            }
        }
    }

    width: 100%;
    height: 700px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    position: relative;

    &:before {
        content: '';
        width: 100%;
        height: 100%;
        backdrop-filter: blur(10px);
        filter: brightness(50%);
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }
}
</style>