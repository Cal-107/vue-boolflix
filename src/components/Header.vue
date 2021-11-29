<template>
  <header>
      <input type="text" placeholder="Cosa vuoi cercare?">
      <button class="searchBtn">Search</button>
  </header>
</template>

<script>
export default {
    name: 'Header',
}
</script>

<style lang="scss" scoped>
header{
    padding: 1rem;
    button {
        margin-left: 1rem;
    }
}
</style>