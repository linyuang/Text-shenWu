<template>
  <div class="cover" :style="{height:height + 'px'}">
    <div class="coverImageBox">
      <img class="coverImage" src="../assets/logo.png">
    </div>
  </div>
</template>
<script>
  const nativeHeight = window.innerHeight;
  export default{
    data(){
      return{
        height:'0px'
      }
    },
    methods:{
      push(){
        setTimeout(() => {
            this.$router.push('/home')
        },2000)
      },
      GetHeight(){
          this.height = nativeHeight;
      }
    },
    created(){
      this.GetHeight();
    },
    mounted(){
        this.$nextTick(() => {
          this.push();
        })
    }
  }
</script>
<style>
  .cover{
    display: flex;
    flex: 1;
    width: 16rem;
    justify-content: center;
    align-items: center;
    background: linear-gradient(to top,rgb(255,255,255),rgb(86,160,225));

    display: -webkit-flex;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .coverImageBox{
    display: flex;
    justify-content: center;
    align-items: center;
    width: 8rem;
    height: 8rem;

    display: -webkit-flex;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .coverImage{
    width:6rem;
    height: 6rem;
  }
</style>
