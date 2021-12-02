<template>
  <header>
      <section class="d-flex align-items-center w-50">
        <img src="https://fontmeme.com/permalink/211201/0d3bf00f62984d25d902f2b5c61959bd.png" alt="">
        <nav class="nav-1 px-3" v-show="propArray != 0 || propArray2 != 0">
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
    <nav class="nav-2" v-show="(propArray != 0) || (propArray2 != 0)">
        <input
            type="text" 
            placeholder="Search Movies or Series"
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
    props: {
        propArray: Array,
        propArray2: Array,
    }
}
</script>

<style lang="scss" scoped>
header {
    padding: 1rem 2.5rem;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-image: linear-gradient(to top, rgba(245, 246, 252, 0) , rgba(0, 0, 0, 1), rgba(0, 0, 0, 1));
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
            transition: font-size 1s;
            &:focus {
                outline: none;
                border-bottom: .5px solid white;
                padding: .5rem 2rem;
                font-size: 1.5rem;
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