<template>
  <div class="loader">
      <div class="text">
          We're coming..         
      </div>
      <div class="img-box">
          <img src="https://fontmeme.com/permalink/211201/0d3bf00f62984d25d902f2b5c61959bd.png" alt="">
      </div>

      
      
  </div>
</template>

<script>
export default {
    name: 'Loader',
}
</script>

<style lang="scss" scoped>

.loader{
    height: 100%;
    display: flex;
    flex-direction: column;
    text-align: center;
    justify-content: center;
    .text {
        font-size: 4rem;
    }
    .img-box {
        padding: 2rem;
        img {
            width: 500pxpx;
            animation: rotate 1s infinite alternate;
            @keyframes rotate {
                from {
                    transform: rotate(0deg);
                }
                to {
                    transform: rotate(359deg);
                }
            }
        }
    }
}
</style>