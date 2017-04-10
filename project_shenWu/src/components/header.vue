<template>
  <div class="header">
    <div class="contentBox">
      <a class="officialWebButton" href="http://www.duoyi.com/">
        <img class="officialLogo" src="../assets/official_logo.png">
      </a>
    </div>
    <div class="contentBox">
      <img class="appLogo" src="../assets/app_logo.png">
    </div>
    <div class="contentBox">
      <img class="appLogoText" src="../assets/app_logo_text.png">
    </div>
  </div>
</template>
<script>
  export default{
      data(){
          return{
          }
      }
  }
</script>
<style scoped>
  .header{
    display: flex;
    flex-direction: row;
    position: fixed;
    top: 0;
    width: 16rem;
    height: 2rem;
    background-color: rgb(230,204,135);

    display: -webkit-flex;
    -webkit-flex-direction: row;
  }
  .contentBox{
    display: flex;
    flex: 1;
    justify-content: center;
    align-items: center;

    display: -webkit-flex;
    -webkit-flex: 1;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .contentBox:first-child,.contentBox:last-child{
    flex: 2;
  }
  .officialLogo{
    width:auto;
    height: 0.9rem;
  }
  .appLogoText{
    width: auto;
    height: 1.5rem;
  }
  .appLogo{
    width: auto;
    height: 2rem;
    margin-top: 1rem;
  }
</style>
