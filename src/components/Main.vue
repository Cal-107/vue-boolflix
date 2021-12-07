<template>
  <main>
    <section class="content p-5" v-if="condLoader">
        <!-- <Loader v-show="condLoader2" /> -->
        <section class="my-box d-flex flex-column">
      
          <div class="d-flex flex-column overflow-X pb-4">
          
              <h1 class="p-3 align-self-start" v-show="propArray != 0">
                  <img :src="require(`../assets/netflix-seeklogo.com.svg`)" alt="">
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

          <div class="d-flex flex-column overflow-X pb-4" >
            <h1 class="p-3 align-self-start" v-show="propArray2 != 0">
                <img :src="require(`../assets/netflix-seeklogo.com.svg`)"    alt=""> 
                <span class="text-uppercase fs-3">Series</span>
            </h1>
            <div class="d-flex scroll-remove">
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
    </section>

    <section class="banner d-flex justify-content-center align-items-center flex-column" v-else>
        <div class="landing-page">
            <h1>Search something to see..</h1>
            <input
                type="text" 
                placeholder="Search Movies or Series"
                v-model.trim="inputValue"
                @keyup.enter="$emit( 'searchInput', inputValue)"
            />
        </div>
    </section>
  </main>
</template>

<script>

import Card from '@/components/Card';
// import Loader from '@/components/Loader.vue';

export default {
    name: 'Main',
    data() {
        return {
            inputValue: '',
        }
    },
    components: {
        Card,
        // Loader,
    },
    props: {
        propArray: Array,
        propArray2: Array,
    },
    computed: {
        condLoader() {
            return this.propArray != 0 || this.propArray2 != 0;
        },
        
        // condLoader2() {
        //     return this.propArray == 0 || this.propArray2 == 0;
        // }
    },
}
</script>

<style lang="scss" scoped>
main {
    .content {
        width: 100%;
        min-height: 100vh;
        color: #fff;
        background-image: linear-gradient(to top, rgba(0, 0, 0, .8) , rgba(0, 0, 0, 1));
        background-attachment: fixed;
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
    
    .banner {
        background-image: linear-gradient(to top, rgba(255, 255, 255, 0), rgba(0, 0, 0, .1), rgba(0, 0, 0, .9)), url('../assets/log-in-wallpaper.png');
        background-size: cover;
        background-repeat: no-repeat;
        min-height: 100vh;
        color: #fff;
        .landing-page {
            width: 600px;
            height: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border-radius: 10px;
            background-color: rgba(0, 0, 0, .82);
            }
            input {
            margin-top: 3rem;
            border: none;
            background-color: transparent;
            color: #fff;
            transition: transform 1s ease;
            &:focus {
                outline: none;
                border-bottom: .5px solid white;
                padding: .5rem 2rem;
                transform: scale(1.2);
            }
        }
    }
}
</style>