<template>
  <section>
       <div v-if="image != null || image != undefined">
            <img :src="`https://image.tmdb.org/t/p/w185/${image}`" :alt="title">
       </div>
       <div class="img-not-found" v-else>
           Not Image Found :(
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
           {{ number }}
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