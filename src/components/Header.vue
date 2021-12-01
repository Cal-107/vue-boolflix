<template>
  <header>
    <img src="https://fontmeme.com/permalink/211201/0d3bf00f62984d25d902f2b5c61959bd.png" alt="">

    <nav>
        <input 
            type="text" 
            placeholder="Search Movie"
            v-model.trim="inputValue"
            @keyup.enter="$emit( 'searchInput', inputValue)"
        />
        <button
            @click.prevent="$emit( 'searchInput', inputValue)"
            class="searchBtn"
        >
                Search
        </button>
    </nav>
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
    height: 8%;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #000;
    button {
        margin-left: 1rem;
    }
}
</style>