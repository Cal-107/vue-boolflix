<template>
  <header>
      <form>
        <input 
            type="text" 
            placeholder="Search Movie"
            v-model="inputValue"
            @keyup.enter="$emit( 'searchInput', inputValue)"
        />
        <button
            type="submit"
            @click.prevent="$emit( 'searchInput', inputValue), (clearSearch() )"
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
    methods: {
        clearSearch() {
            this.inputValue = '';
        }
    }
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