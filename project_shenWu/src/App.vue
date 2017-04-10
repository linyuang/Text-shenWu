<template>
  <div id="app">
    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>

  </div>
</template>

<script>
  window.fontSize = (window.innerWidth  * 100) / 1600;
  document.querySelector('html').style.fontSize = fontSize + 'px';
  window.baseUrl = 'http://image.duoyi.com/';
  export default {
    data(){
        return{}
    },
    methods:{
    },
  }
</script>

<style>
  html,body{
    margin: 0;
    padding: 0;
    height: 100%;
  }
  p{
    margin: 0.1rem;
  }
  #app {
    display: flex;
    flex: 1;
    width: 16rem;
    height: auto;
    overflow: auto;

    display: -webkit-flex;
    -webkit-flex: 1;
  }
  .slideL-enter-active{
    -webkit-animation: slideL-in 1s;
    animation: slideL-in 1s;
  }
  .slideL-leave-active{
    -webkit-animation: slideL-out 1s;
    animation: slideL-out 1s;
  }
  .slideR-enter-active{
    -webkit-animation: slideR-in 1s;
    animation: slideR-in 1s;
  }
  .slideR-leave-active{
    -webkit-animation: slideR-out 1s;
    animation: slideR-out 1s;
  }
  .fade-enter-active{
    -webkit-animation: fade-in .7s;
    animation: fade-in .7s;
  }
  .fade-leave-active{
    -webkit-animation: fade-out .7s;
    animation: fade-out .7s;
  }
  .featuresL-enter-active{
    -webkit-animation:featuresL-in 1s;
    animation: featuresL-in 1s
  }
  .featuresL-leave-active{
    -webkit-animation: featuresL-out 1s;
    animation: featuresL-out 1s;
  }

  @keyframes featuresL-in {
    0% {
      transform: translateX(100%);
      opacity: 0;
      -webkit-transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
      opacity: 1;
      -webkit-transform: translateX(0);
    }
  }
  @-webkit-keyframes featuresL-in {
    0% {
      transform: translateX(100%);
      opacity: 0;
      -webkit-transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
      opacity: 1;
      -webkit-transform: translateX(0);
    }
  }
  @keyframes featuresL-out {
    0% {
      transform: translateX(0);
      opacity: 1;
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
      opacity: 0;
      -webkit-transform: translateX(-100%);
    }
  }
  @-webkit-keyframes featuresL-out {
    0% {
      transform: translateX(0);
      opacity: 1;
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
      opacity: 0;
      -webkit-transform: translateX(-100%);
    }
  }
  @keyframes slideR-in {
    0% {
      transform: translateX(-100%);
      -webkit-transform: translateX(-100%);
    }
    100% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
  }
  @-webkit-keyframes slideR-in {
    0% {
      transform: translateX(-100%);
      -webkit-transform: translateX(-100%);
    }
    100% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
  }
  @keyframes slideR-out {
    0% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(100%);
      -webkit-transform: translateX(100%);
    }
  }
  @-webkit-keyframes slideR-out {
    0% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(100%);
      -webkit-transform: translateX(100%);
    }
  }
  @keyframes slideL-in {
    0% {
      transform: translateX(100%);
      -webkit-transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
  }
  @-webkit-keyframes slideL-in {
    0% {
      transform: translateX(100%);
      -webkit-transform: translateX(100%);
    }
    100% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
  }
  @keyframes slideL-out {
    0% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
      -webkit-transform: translateX(-100%);
    }
  }
  @-webkit-keyframes slideL-out {
    0% {
      transform: translateX(0);
      -webkit-transform: translateX(0);
    }
    100% {
      transform: translateX(-100%);
      -webkit-transform: translateX(-100%);
    }
  }
  @keyframes fade-in {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  @-webkit-keyframes fade-in {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
  @keyframes fade-out {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
  @-webkit-keyframes fade-out {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
</style>
