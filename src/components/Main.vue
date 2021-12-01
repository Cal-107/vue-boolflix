<template>
  <main class="p-5">
    <section class="my-box d-flex flex-column" v-if="(propArray != 0) || (propArray2 != 0)">
      <div class="d-flex flex-column overflow-X pb-4">
          <h1 class="p-3 align-self-start" v-show="propArray != 0">
              <img src="https://upload.wikimedia.org/wikipedia/commons/0/0c/Netflix_2015_N_logo.svg" alt="">
              <span class="text-uppercase fs-3">Movies</span>
          </h1>
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
                    :text2="movie.overview"
                />
            </ul>
          </div>
      </div>
    
      <div class="d-flex flex-column overflow-X pb-4">
        <h1 class="p-3 align-self-start" v-show="propArray2 != 0">
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/0c/Netflix_2015_N_logo.svg" alt=""> 
            <span class="text-uppercase fs-3">Series</span>
        </h1>
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
                    :text2="serie.overview"
                />
            </ul>
        </div>
      </div>
    </section>
    <!-- <section v-else>
        <h1>
            Choisee your movie
        </h1>
    </section> -->
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
    color: #fff;
    background-color: #141414;
    // .wallapper {
    //     img {
    //         width: 100%;
    //         height: 100%;
    //     }
    // }
    .my-box {
        margin-top: 3rem;
        .overflow-X {
            overflow-x: scroll;
        }
        ul {
            padding-left: 2.8rem;
        }
        h1 {
            text-align: center;
            letter-spacing: .7rem;
            font-weight: bold;
            img {
                width: 2rem;
                margin-right: 1.5rem;
            }
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