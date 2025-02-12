<template>
    <header>
      <img src="@/assets/images/logo.png" class="logo" alt="">
      <div class="menu-mobile">
        <img src="@/assets/images/avatar.png" class="menu-mobile__avatar" alt="">
        <IconMenuDeep size="28" />        
      </div>
    </header>
</template>

<script setup lang="ts">

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
        width: 30px;
        border-radius: 50%;
      }
    }
  }
  
</style>