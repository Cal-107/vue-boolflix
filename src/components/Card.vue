<template>
  <section>
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
</style>