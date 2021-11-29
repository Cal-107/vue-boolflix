<template>
  <main>
    <ul v-for="(movie, i) in propArray" :key="`movie-${i}`">
        <Card 
            :title="movie.title"
            :subTitle="movie.original_title"
            :text="movie.original_language"
            :number="movie.vote_average"
        />
    </ul>
  </main>
</template>

<script>

import Card from '@/components/Card';

export default {
    name: 'Main',

    components: {
        Card,
    },
    props: {
        propArray: Array,
    },
}
</script>

<style lang="scss" scoped>
</style>