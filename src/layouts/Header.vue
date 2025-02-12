<template>
    <header>
      <img src="@/assets/images/logo.png" class="logo" alt="">

      <div class="menu-mobile">
        <img src="@/assets/images/avatar.png" class="menu-mobile__avatar" alt="">
        <IconMenuDeep size="28" />
        <!-- <img src="@/assets/images/icons/menu.svg" class="menu-mobile__hamburguer" alt=""> -->
        
      </div>
    </header>
</template>

<script setup>

import {IconMenuDeep} from '@tabler/icons-vue'
 

</script>

<style lang="scss">

  @use '@/scss/mixings.scss';

  header{
    @include mixings.flexbox(row,space-between,center);
    padding: 15px 20px;
    position: sticky;
    .logo{
      width: 100px;
    }   
    .menu-mobile{
      @include mixings.flexbox(row,space-between,center);
      gap: 5px;
      &__avatar{
        width: 25px;
        border-radius: 50%;
      }
    }
  }
  
</style>