<template>
  <main class="p-5">
    <section class="my-box d-flex flex-column">
      <div class="d-flex flex-column overflow-scroll">
          <h1 class="p-3 align-self-start">Movies</h1>
          <div class="d-flex">
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
      </div>
    
      <div class="d-flex flex-column overflow-scroll">
        <h1 class="p-3 align-self-start">Series</h1>
        <div class="d-flex">
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
main {
    background-color: #141414;
    height: 92%;
    color: #fff;
    .my-box {
        h1 {
            text-align: center;
        }
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
}
</style>