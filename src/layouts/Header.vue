<template>
    <header>
      <img src="@/assets/images/logo.png" class="logo" alt="">
    </header>
</template>

<style lang="scss">

  @use '@/scss/mixings.scss';

  header{
    @include mixings.flexbox(row,initial,center);
    padding: 15px 20px;
    position: sticky;
    .logo{
      width: 100px;
    }
  }
  
</style>