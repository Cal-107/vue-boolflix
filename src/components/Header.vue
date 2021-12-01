<template>
  <header>
      <section class="d-flex align-items-center w-50">
        <img src="https://fontmeme.com/permalink/211201/0d3bf00f62984d25d902f2b5c61959bd.png" alt="">
        <nav class="nav-1 px-3">
            <ul class="d-flex justify-content-between">
                <li><a href="/">Home</a></li>
                <li><a href="/">Serie TV</a> </li>
                <li><a href="/">Film</a> </li>
                <li><a href="/">Nuovi e Popolari</a> </li>
                <li><a href="/">La mia lista</a></li>
                <li><a href="/">Guarda di nuovo</a> </li>
            </ul>
        </nav>
      </section>
    <nav class="nav-2">
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
                <i class="fas fa-search"></i>
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
    padding: 1rem 2.5rem;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgb(0,0,0);
    background: linear-gradient(180deg, rgba(0,0,0,1) 0%, rgba(0,0,0,0) 100%);
    position: fixed;
    z-index: 1;
    .nav-1 {
        color: #fff;
        ul {
            margin: 0;
            padding: 0;
            font-weight: 100;
            li {
                font-size: .9rem;
                padding-right: 1rem;
                a {
                    color: #fff;
                }
            }
        }
    }
    img {
        width: 150px;
    }.nav-2 {
        input {
            border: none;
            background-color: transparent;
            color: #fff;
            &:focus {
                outline: none;
                border-bottom: 1px solid white;
                border-radius: 5px;
            }

        }
        button {
            margin-left: 1rem;
            border: none;
            background-color: transparent;
            color: #fff;
        }
    }
}
</style>