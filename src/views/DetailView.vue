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
            <div class="detail__intro" v-if="movieInfo"
                :style="{ backgroundImage: `url(https://image.tmdb.org/t/p/w500${movieInfo.backdrop_path})` }">
                <div class="container">
                    <div class="left play__icon">
                        <img :src="'https://image.tmdb.org/t/p/w500/' + movieInfo.poster_path" alt="영화포스터">
                    </div>
                    <div class="right">
                        <h2>{{ movieInfo.title }}</h2>
                        <p class="desc">
                            {{ movieInfo.overview }}
                        </p>
                        <div class="info">
                            <p class="date">출시 : {{ movieInfo.release_date }} </p>
                            <p class="vote">평점 : {{ movieInfo.vote_average }}</p>
                        </div>
                        <div class="credits">
                            <div v-for="charactor in creditInfo.slice(0, 5)" :key="charactor.id">
                                <img :src="'https://image.tmdb.org/t/p/w500/' + charactor.profile_path" alt="">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import { ref, onMounted } from "vue";
import { useRoute } from 'vue-router';

export default {
    setup() {
        const movieInfo = ref({});
        const creditInfo = ref([]);

        const route = useRoute();
        const apiKey = import.meta.env.VITE_API_KEY;

        const movieInfoFetch = (movieId) => {
            fetch(`https://api.themoviedb.org/3/movie/${movieId}?api_key=${apiKey}&language=ko-KR`)
                .then((response) => response.json())
                .then((res) => {
                    movieInfo.value = res;
                    console.log(movieInfo);
                })
                .catch((err) => {
                    console.log(err)
                })
        }

        const creditInfoFetch = (movieId) => {
            fetch(`https://api.themoviedb.org/3/movie/${movieId}/credits?api_key=${apiKey}&language=ko-KR`)
                .then((response) => response.json())
                .then((res) => {
                    creditInfo.value = res.cast;
                    console.log(creditInfo);
                })
                .catch((err) => {
                    console.log(err);
                })
        }

        onMounted(() => {
            const movieId = route.params.movieId;
            movieInfoFetch(movieId);
            creditInfoFetch(movieId);
        })

        return { movieInfo, creditInfo };
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