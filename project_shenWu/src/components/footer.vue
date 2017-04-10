<template>
  <div class="footer">
    <div class="footerLink">
      <a class="fontStyle" href="http://hr.duoyi.com/">招聘信息</a>-
      <a class="fontStyle" href="http://www.duoyi.com/dycommerce/ch/business.shtm">商务合作</a>-
      <a class="fontStyle" href="http://kf.duoyi.com/sw/Login.aspx">客服服务</a>-
      <a class="fontStyle" href="http://www.duoyi.com/">多益游戏</a>
    </div>
    <p class="fontStyle">广州多益网络股份有限公司</p>
    <p class="fontStyle">ICP粤B2-20060723</p>
    <p class="fontStyle">文网游备字：[2016]C-RPG0798号</p>
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
  .footer{
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: center;
    width: 16rem;
    height: 6rem;
    padding-bottom: 0.5rem;
    background: linear-gradient(rgb(255,255,255),rgb(230,204,135));

    display: -webkit-flex;
    -webkit-flex-direction: column;
    -webkit-justify-content: flex-end;
    -webkit-align-items: center;
    background: -webkit-linear-gradient(rgb(255,255,255),rgb(230,204,135));
  }
  .footerLink{
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 14rem;
    height: 1rem;

    display: -webkit-flex;
    -webkit-flex-direction: row;
    -webkit-justify-content: center;
    -webkit-align-items: center;
  }
  .footerLink a{
    text-decoration: none;
  }
  .fontStyle{
    font-size: 0.5rem;
    color: #000000;
  }
</style>
