<template>
  <div id="app">
    <Header @searchInput="getList" :propArray="movieList" :propArray2="seriesList"/>

    <Main :propArray="movieList" :propArray2="seriesList" @searchInput="getList" />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
    components: {
      Header,
      Main,
    },

  data() {
      return {
          movieList: [],
          seriesList: [],
          inputText: '',
      }
  },

  methods: {
      getList(text) {
        if (text === '') {
          this.movieList = [];
          this.seriesList = [];
        } else {
          axios
          .get ('https://api.themoviedb.org/3/search/movie', {
              params: {
                  api_key: '7872b69ec498a7e0e4e9f9dadbe23059',
                  query: text,
              },
          })
          .then (response => {
              this.movieList = response.data.results;
          })
          .catch (err => console.log(err));
          
          axios
          .get ('https://api.themoviedb.org/3/search/tv', {
              params: {
                  api_key: '7872b69ec498a7e0e4e9f9dadbe23059',
                  query: text,
              },
          })
          .then (response => {
              this.seriesList = response.data.results;
          })
          .catch (err => console.log(err));
        }
      },

      setValue (text) {
        this.inputText = text;
      },
  }
}
</script>

<style lang="scss">
@import '@/styles/globals';
</style>