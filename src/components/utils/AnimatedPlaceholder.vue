<template>
  <div class="placeholder">&nbsp;</div>
</template>

<script setup>
  // eslint-disable-next-line no-undef
  defineProps({
    height: { type: String},
    width: { type: String},
    margin: { type: String, default: '0'},
    borderTopLeft:  { type: String,default: '5px'},
    borderTopRight: { type: String,default: '5px'},
    borderBottomLeft:  { type: String,default: '5px'},
    borderBottomRight: { type: String,default: '5px'},
  })
</script>

<style lang="scss" scoped>

  .placeholder {
    height: v-bind(height);
    width: v-bind(width);
    margin: v-bind(margin);
    border-top-left-radius: v-bind(borderTopLeft);
    border-top-right-radius: v-bind(borderTopRight);
    border-bottom-left-radius: v-bind(borderBottomLeft);
    border-bottom-right-radius: v-bind(borderBottomRight); 
    background-image: linear-gradient(
      to right,
      #d6d7d8 0%,
      #e2e3e4 10%,
      #d6d7d8 20%,
      #d6d7d8 100%
    );
    background-size: 200% 100%;
    box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
    animation: bgAnimate 1.2s linear infinite;
  }
</style>
