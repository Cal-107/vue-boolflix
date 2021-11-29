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
           {{ subText }}
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
        subText: String,
    }
}
</script>

<style lang="scss" scoped>
</style>