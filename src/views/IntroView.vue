<template>
    <div class="intro">
      <img src="@/assets/images/logo.png" class="logo-container">
    </div>
  </template>

  <script setup lang="ts">

import router from '@/router'

    setTimeout(()=>{
        router.push({name:'home'})
    },3500)
  


  </script>
  
<style lang="scss">
  .intro {
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    overflow: hidden;
    position: relative;
  }
  
  .logo-container {
    position: absolute;
    animation: fallBounce 2s ease-in-out forwards, fadeOut 0.5s ease-in-out 2.5s forwards;
  }
  
  @keyframes fallBounce {
    0% {
      transform: translateY(-50vh); 
    }
    60% {
      transform: translateY(0);
    }
    75% {
      transform: translateY(-20px); 
    }
    85% {
      transform: translateY(0);
    }
    92% {
      transform: translateY(-10px); 
    }
    100% {
      transform: translateY(0);
    }
  }
  
  @keyframes fadeOut {
    0% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }
  </style>
  