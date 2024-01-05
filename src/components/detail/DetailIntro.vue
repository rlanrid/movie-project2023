<template>
    <div class="detail__intro"
        :style="{ backgroundImage: 'url(https://image.tmdb.org/t/p/w500/' + movie.backdrop_path + ')' }">
        <div class="container">
            <div class="left play__icon">
                <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" alt="영화포스터">
            </div>
            <div class="right">
                <div>
                    <h2 class="title">{{ movie.title }}</h2>
                </div>
                <p class="tag__line">{{ movie.tagline }}</p>
                <div class="info">
                    <p class="date">{{ movie.release_date }}</p>
                    <p class="vote">{{ movie.vote_average }}</p>
                </div>
                <div class="desc">
                    <p>{{ movie.overview }}</p>
                </div>
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
    display: flex;
    align-items: center;
    justify-content: center;

    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        z-index: 10;

        @media(max-width: 780px) {
            margin: 0;
            flex-direction: column;
            padding-top: 30px;
        }

        .left {
            width: 20vw;
            min-width: 275px;
        }

        .right {
            width: calc(100% - 40vw);
            margin-left: 2%;

            @media(max-width: 780px) {
                margin-top: 5vw;
                width: 100%;
            }

            .tag__line {
                margin-bottom: 2vw;
            }

            .info {
                margin-bottom: 2vw;
                display: flex;

                p {
                    &:first-child {
                        position: relative;

                        &::after {
                            content: '';
                            position: absolute;
                            width: 1px;
                            height: 22px;
                            right: -7.5px;
                            top: 0;
                            opacity: 0.9;
                            background-color: var(--white300);

                            @media(max-width:780px) {
                                height: 17px;
                            }
                        }
                    }

                    &:last-child {
                        margin-left: 14px;
                    }
                }
            }

            .title {
                width: 100%;
                font-size: 3rem;
                margin-bottom: 10px;
                line-height: 1;
                font-weight: 700;
            }

            p {
                font-size: 16px;

                @media(max-width:780px) {
                    font-size: 14px;
                }
            }

            .desc {
                @mixin line($line) {
                    overflow: hidden;
                    text-overflow: ellipsis;
                    display: -webkit-box;
                    -webkit-line-clamp: $line;
                    -webkit-box-orient: vertical;
                }

                margin-bottom: 2vw;
                @include line(5);
            }

            .credits {
                display: flex;
                align-items: center;

                div {
                    width: 6vw;
                    margin-right: 15px;

                    @media(max-width:780px) {
                        width: 19%;
                    }
                }
            }
        }
    }

    width: 100%;
    height: 90vh;
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