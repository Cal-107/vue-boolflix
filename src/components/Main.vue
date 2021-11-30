<template>
  <main>
    <ul v-for="movie in propArray" :key="movie.id">
        <Card 
            :image="movie.poster_path"
            :title="movie.title"
            :subTitle="movie.original_title"
            :text="movie.original_language"
            :number="movie.vote_average"
        />
    </ul>

    <ul v-for="serie in propArray2" :key="serie.id">
        <Card 
            :title="serie.name"
            :subTitle="serie.original_name"
            :text="serie.original_language"
            :number="serie.vote_average"
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
        propArray2: Array,
    },
}
</script>

<style lang="scss" scoped>
</style>