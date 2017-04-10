<template>
  <v-touch class="scroll" v-show="scrollShow" @tap="toTop()">
    <img class="scrollUpImage" src="../assets/scroll_up.png">
  </v-touch>
</template>
<script>
  export default{
    data(){
      return{
          scrollShow:false
      }
    },
    methods:{
      toTop(){
        document.body.scrollTop = 0;
      },
      scrollListener(){
        this.scrollShow = (window.scrollY > 8 * window.fontSize) ? true : false;
      }
    },
    mounted(){
        this.$nextTick(() => {
            window.addEventListener('scroll',this.scrollListener);
        })
    }
  }
</script>
<style>
  .scroll{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 1.5rem;
    height: 1.5rem;
    background-color: #ffffff;
    border-radius: 0.5rem;
    border: 0.2rem solid #000000;

    display: -webkit-flex;
    -webkit-justify-content: center;
    -webkit-align-items: center;
    -webkit-border-radius: 0.5rem;
  }
  .scrollUpImage{
    width: 0.8rem;
    height: auto;
  }
</style>
