<template>
  <section>
      <li>
           {{ title }}
       </li>
       <li>
           {{ subTitle }}
       </li>
       <li>
           {{ text }}
       </li>
       <li>
           {{ number }}
       </li>
  </section>
</template>

<script>
export default {
    name: 'Card',
    props: {
        title: String,
        subTitle: String,
        text: String,
        number: Number,
    }
}
</script>

<style lang="scss" scoped>
</style>