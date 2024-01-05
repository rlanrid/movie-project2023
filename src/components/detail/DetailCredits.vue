<template>
    <div class="detail__credits">
        <div class="container">
            <h2>출연진</h2>
            <div class="credits">
                <div v-for="(movies, index) in movie.data.cast.slice(0, 5)" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + movies.profile_path" alt="프로필사진">
                    <div class="info">
                        <div class="name">{{ movies.original_name }}</div>
                        <div class="role">{{ movies.character }}</div>
                    </div>
                </div>
            </div>
            <h2>제작진</h2>
            <div class="credits">
                <div v-for="(movies, index) in movie.data.crew.slice(0, 5)" :key="index">
                    <img v-if="movies.profile_path" :src="'https://image.tmdb.org/t/p/w500/' + movies.profile_path"
                        :alt="movies.name">
                    <img v-else src="../../assets/img/profile.jpg">
                    <div class="info">
                        <div class="name">{{ movies.original_name }}</div>
                        <div class="role">{{ movies.department }}</div>
                    </div>
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
.detail__credits {
    margin-bottom: 3rem;

    .container {
        .credits {
            width: 100%;
            max-width: 1300px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            // border: 1px solid var(--white600);

            .info {
                width: 100%;
                text-align: center;
                color: var(--white);
                height: 100px;

                .name {
                    width: 100%;
                    font-weight: 800;
                    text-align: center;
                    word-break: break-all;
                }

                .role {
                    width: 100%;
                    font-size: 14px;
                    text-align: center;
                }

                @media(max-width: 780px) {
                    .name {
                        font-size: 12px;
                    }

                    .role {
                        font-size: 10px;
                    }
                }
            }

            div {
                width: 19%;
            }
        }
    }
}
</style>
