<template>
  <main>
    <section class="my-box">
      <div>
          <h1 v-show="propArray2 != 0"> Movies List</h1>
          <ul 
                class="movies" 
                v-for="movie in propArray" 
                :key="movie.id"
            >
              <Card 
                  :image="movie.poster_path"
                  :title="movie.title"
                  :subTitle="movie.original_title"
                  :text="movie.original_language"
                  :number="movie.vote_average"
              />
          </ul>
      </div>
    
      <div>
        <h1 v-show="propArray2 != 0"> Series List </h1>
        <ul 
            class="series" 
            v-for="serie in propArray2" 
            :key="serie.id"
        >
            <Card 
                :image="serie.poster_path"
                :title="serie.name"
                :subTitle="serie.original_name"
                :text="serie.original_language"
                :number="serie.vote_average"
            />
        </ul>
      </div>
    </section>  
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
.my-box {
    h1 {
        text-align: center;
    }
    display: flex;
    .movies {
        section {
            display: flex;
            flex-direction: column;
            img {
                align-self: center;
            }
        }
    }
    .series {
        section {
            display: flex;
            flex-direction: column;
        }
    }
}
</style>