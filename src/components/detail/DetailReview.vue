<template>
    <div class="detail__review">
        <div class="container">
            {{ movie.results }}
        </div>
    </div>
</template>

<script>
export default {
    props: {
        movie: {
            type: Object,
            require: true,
        }
    }
}
</script>

<style lang="scss"></style>