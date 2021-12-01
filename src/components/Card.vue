<template>
  <section>
      <div class="all-box">
            <div class="img-box" v-if="image != null || image != undefined">
                 <img class="img-poster" :src="`https://image.tmdb.org/t/p/w342/${image}`" :alt="title">
            </div>
            <div class="img-not-found" v-else>
                Image Not Found :(
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
        .img-poster, 
        .img-not-found,
        .info-box {
            transition: all .3s ease-in-out;
            border-radius: 8px;
        }
        &:hover .info-box {
           opacity: 100;
           transform: scale(1.05);
        }
        &:hover .img-poster, 
        &:hover .img-not-found {
            filter: blur(10px) brightness(0.3);
            transform: scale(1.05);
        }
        .info-box {
            position: absolute;
            top: 8%;
            left: 0;
            opacity: 0;
            text-align: center;
            transform: translateY(100px);
            li {
                font-size: 12px;
                .text-custom {
                    font-weight: 800;
                    letter-spacing: 2px;
                }
            }
            .fa-star {
                margin-left: .5rem;
                color: yellow;
            }
        }
        .img-not-found {
            width: 342px;
            height: 513px;
            background: #000;
            color: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    }

}
</style>