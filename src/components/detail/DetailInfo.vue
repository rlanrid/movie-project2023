<template>
    <div class="detail__info">
        <div class="container">
            <h2>정보</h2>
            <div class="genres">
                <i>장르 : </i>
                <p v-for="(movies, index) in movie.genres" :key="index">
                    {{ movies.name }}
                </p>
            </div>
            <div class="release">
                <i>개봉일 : </i>
                <p>{{ movie.release_date }}</p>
            </div>
            <div class="runtime">
                <i>상영시간 : </i>
                <p>{{ movie.runtime }}</p>
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
.detail__info {
    margin-top: 3rem;
    margin-bottom: 3rem;

    .container {
        p {
            display: inline-block;
        }

        .genres {
            p {
                display: inline;
                margin-right: 10px;
                position: relative;

                &::after {
                    content: '';
                    width: 2px;
                    height: 16px;
                    position: absolute;
                    right: -5px;
                    bottom: 0;
                    background-color: var(--white);
                    transform: rotate(25deg);
                }

                &:last-child {
                    &::after {
                        display: none;
                    }
                }
            }
        }
    }
}
</style>