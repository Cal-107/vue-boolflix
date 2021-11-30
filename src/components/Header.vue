<template>
  <header>
      <form>
        <input 
            type="text" 
            placeholder="Search Movie"
            v-model.trim="inputValue"
            @keyup.enter="$emit( 'searchInput', inputValue)"
        />
        <button
            type="submit"
            @click.prevent="$emit( 'searchInput', inputValue)"
            class="searchBtn"
        >
                Search
        </button>
      </form>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            inputValue: '',
        }
    },
}
</script>

<style lang="scss" scoped>
header {
    padding: 1rem;
    button {
        margin-left: 1rem;
    }
}
</style>