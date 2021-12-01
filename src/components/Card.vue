<template>
  <section>
       <div v-if="image != null || image != undefined">
            <img :src="`https://image.tmdb.org/t/p/w185/${image}`" :alt="title">
       </div>
       <div class="img-not-found" v-else>
           Image Not Found :(
       </div>
       <li>
           {{ title }}
       </li>
       <li>
           {{ subTitle }}
       </li>
       <li>
           <img v-if="getFlags" :src="require(`../assets/${text}.png`)" :alt="text">
           <span v-else> {{ text }}</span>
       </li>
       
       <li>
           <i v-for="(number, i) in getVote" :key="`vote-${i}`" class="fas fa-star"></i>

           <i v-for="(number, i) in 5 - getVote" :key="`vote-2-${i}`" class="far fa-star"></i>
       </li>
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
    .img-not-found {
        width: 185px;
        height: 270px;
        background: #000;
        color: #fff;
        display: flex;
        justify-content: center;
        align-items: center;
    }
}
</style>