<template>
    <div class="detail__intro"
        :style="{ backgroundImage: 'url(https://image.tmdb.org/t/p/w500/' + movie.backdrop_path + ')' }">
        <div class="container">
            <div class="left play__icon">
                <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" alt="영화포스터">
            </div>
            <div class="right">
                <h2>{{ movie.title }}</h2>
                <p class="desc">
                    {{ movie.overview }}
                </p>
                <div class="info">
                    <p class="date">출시 : {{ movie.release_date }}</p>
                    <p class="vote">평점 : {{ movie.vote_average }}</p>
                </div>
                <!-- <div class="credits">
                    <div>
                        <img src="https://image.tmdb.org/t/p/w500/q21uuCtTioIVcGc3a1Q0DpdcNMO.jpg" alt="">
                    </div>
                    <div>
                        <img src="https://image.tmdb.org/t/p/w500/s2Ouz4b7xqDH72aU48TSW5zS40v.jpg" alt="">
                    </div>
                    <div>
                        <img src="https://image.tmdb.org/t/p/w500/a5r4MtoL5jU4DtCp0BtzwEAtfyL.jpg" alt="">
                    </div>
                    <div>
                        <img src="https://image.tmdb.org/t/p/w500/oWkitw5jzILwb775CVGjsqMSrqz.jpg" alt="">
                    </div>
                    <div>
                        <img src="https://image.tmdb.org/t/p/w500/9lEbP0scP8vjNa4hYmAg4UgMQky.jpg" alt="">
                    </div>
                </div> -->
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        movie: {
            type: Object,
            required: true,
        }
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
            flex-wrap: wrap;
            // flex-direction: column;
            // justify-content: space-between;

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