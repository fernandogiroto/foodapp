<template>
    <div class="search-input">
      <span class="icon">
        <slot name="icon"></slot>
      </span>
      <input 
        type="text" 
        v-model="searchQuery" 
        placeholder="Search dishes, restaurants"
      />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const searchQuery = ref('');
  </script>
  
  <style lang="scss" scoped>
  .search-input {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 8px;
    background-color: #fff;
    width: 100%;
    max-width: 400px;
  
    .icon {
      display: flex;
      align-items: center;
      justify-content: center;
      color: #888;
    }
  
    input {
      border: none;
      outline: none;
      font-size: 16px;
      flex: 1;
      background: transparent;
    }
  }
  </style>
  