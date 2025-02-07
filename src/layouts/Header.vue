<template>
    <header>HEADER</header>
</template>

<style lang="scss">

  @use '@/scss/mixings.scss';

  header{
    @include mixings.flexbox(row,initial,center);
    padding: 25px;
  }
  
</style>