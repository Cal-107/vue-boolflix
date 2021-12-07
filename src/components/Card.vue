<template>
  <section>
      <div class="all-box">
            <div class="img-box" v-if="image != null || image != undefined">
                 <img class="img-poster" :src="`https://image.tmdb.org/t/p/w342/${image}`" :alt="title">
            </div>
            <div class="img-not-found" v-else>
                <img src="https://cdn2.iconfinder.com/data/icons/symbol-blue-set-3/100/Untitled-1-94-512.png" alt="">
            </div>

            <div class="info-box">
                <li>
                    <span class="text-custom">Titolo: </span> {{ title }}
                </li>
                <li>
                    <span class="text-custom">Titolo Originale: </span> {{ subTitle }}
                </li>
                <!-- <li>
                    <img v-if="getFlags" :src="require(`../assets/${text}.png`)" :alt="text">
                    <span v-else> {{ text }}</span>
                </li> -->
                <li>
                    <span class="text-custom">Voto: </span>
                    <i v-for="(number, i) in getVote" :key="`vote-${i}`" class="fas fa-star"></i>
                    <i v-for="(number, i) in 5 - getVote" :key="`vote-2-${i}`" class="far fa-star"></i>
                </li>
                <li>
                    <span class="text-custom">Descrizione: </span> {{ text2 }}
                </li>
                <li>
                    <span>Nome Attore</span> {{ nameActor }}
                </li>
            </div>
      </div>
  </section>
</template>

<script>
export default {
    name: 'Card',
    data() {
        return {
            languagesFlags: ['it', 'en'],
        }
    },

    computed: {
        getFlags() {
            return this.languagesFlags.includes(this.text)
        },

        getVote() {
            return Math.ceil( this.number / 2)
        }
    },
    
    props: {
        image: String,
        title: String,
        subTitle: String,
        text: String,
        number: Number,
        text2: String,
        nameActor: String,
    },
}
</script>

<style lang="scss" scoped>
li {
    img {
        width: 30px;
    }
}
section {
    position: relative;
    .all-box {
        .img-poster {
            max-height: 513px;
            cursor: pointer;
        }
        .img-poster, 
        .img-not-found,
        .info-box {
            transition: all .3s ease-in-out;
            border-radius: 8px;
            cursor: pointer;
        }
        &:hover .info-box {
           opacity: 100;
           transform: translateY(40px);
        }
        &:hover .img-poster, 
        &:hover .img-not-found {
            transform: translateY(-25px);
            filter: blur(10px) brightness(0.5);
        }
        .info-box {
            position: absolute;
            top: 0;
            left: 0;
            opacity: 0;
            li {
                font-size: 12px;
                .text-custom {
                    font-weight: 800;
                    letter-spacing: 2px;
                }
            }
            .fa-star {
                margin-left: .5rem;
                color: rgb(199, 199, 26);
            }
        }
        .img-not-found {
            img {
                width: 342px;
                height: 513px;
                object-fit: contain;
            }
        }
    }
}
</style>