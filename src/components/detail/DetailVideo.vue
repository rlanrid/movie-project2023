<template>
    <div class="detail__video">
        <div class="video__inner container">
            <h2>영상</h2>
            <div class="video__wrap">
                <div v-for="(video, index) in movie.results.slice(0, 1)" :key="index">
                    <div class="video">
                        <iframe :src="`https://www.youtube.com/embed/${video.key}`" frameborder="0"
                            allowfullscreen></iframe>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
.detail__video {
    margin-bottom: 3rem;

    .video__inner {
        .video__wrap {
            .video {
                position: relative;
                width: 100%;
                padding-bottom: 60%;

                iframe {
                    position: absolute;
                    width: 100%;
                    height: 100%;
                    top: 0;
                    left: 0;
                }
            }
        }
    }
}
</style>
<script>
export default {
    props: {
        movie: {
            type: Object,
            required: true
        }
    },
};
</script>