<template>
    <footer>FOOTER</footer>
</template>

<style lang="scss">

  @use '@/scss/mixings.scss';

  footer{
    @include mixings.flexbox(row,initial,center);
    padding: 25px;
        position: sticky;
  }
  
</style>