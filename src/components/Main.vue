<template>
  <main>
    <ul v-for="(movie, i) in movieList" :key="`movie-${i}`">
       <li>
           {{ movie.title }}
       </li>
       <li>
           {{ movie.original_title }}
       </li>
       <li>
           {{ movie.original_language }}
       </li>
       <li>
           {{ movie.vote_average }}
       </li>
    </ul>
  </main>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Main',
    data() {
        return {
            movieList: null,
        }
    },
    created() {
        this.getMovieList()
    },
    methods: {
        getMovieList() {
            axios
            .get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: '7872b69ec498a7e0e4e9f9dadbe23059',
                    query: 'jurassic',
                    language: 'it-IT',
                },
            })
            .then(response => {
                this.movieList = response.data.results;
            })
            .catch(err => console.log(err));
        },
    }
}
</script>

<style lang="scss" scoped>

</style>