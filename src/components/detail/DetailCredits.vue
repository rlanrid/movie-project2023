<template>
    <div class="detail__credits">
        <div class="container">
            <div class="credits">
                <div v-for="(movies, index) in movie.data.cast.slice(0, 5)" :key="index">
                    <img :src="'https://image.tmdb.org/t/p/w500/' + movies.profile_path" alt="프로필사진">
                    <div class="info">
                        <div class="name">{{ movies.original_name }}</div>
                        <div class="role">{{ movies.character }}</div>
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
    .container {
        .credits {
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            border: 1px solid var(--white600);

            .info {
                text-align: center;
                background-color: var(--white300);
                color: var(--black);

                .name {
                    font-weight: 800;
                }

                .role {
                    font-size: 14px;
                }
            }

            div {
                width: 150px;
                margin-right: 15px;
            }
        }
    }
}
</style>
