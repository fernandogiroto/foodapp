<template>
  <footer class="bottom-to-top--effect">
    <div class="nav-footer">
      <ul class="nav-footer__list">
        <li :class="['nav-footer__list__item', $route.name === 'Home' ? 'nav-footer__list__item--active' : '']">
          <IconToolsKitchen2 size="28" />    
        </li>
        <li :class="['nav-footer__list__item', $route.name === 'Search' ? 'nav-footer__list__item--active' : '']">
          <IconShoppingCart size="28"/>    
        </li>
        <li :class="['nav-footer__list__item', $route.name === 'home' ? 'nav-footer__list__item--active' : '']" @click="goTo('home')">
          <IconHome size="28" :color="$route.name === 'home' ? 'var(--theme-color)' : 'var(--text-color)'"  />    
        </li>
        <li :class="['nav-footer__list__item', $route.name === 'Cart' ? 'nav-footer__list__item--active' : '']">
          <IconBubbleText size="28" />    
        </li>
        <li :class="['nav-footer__list__item', $route.name === 'User' ? 'nav-footer__list__item--active' : '']">
          <IconSearch size="28" />    
        </li>
      </ul>
    </div>
  </footer>
</template>

<script setup lang="ts">

  import router from '@/router'
  import {IconToolsKitchen2,IconShoppingCart,IconHome,IconSearch,IconBubbleText} from '@tabler/icons-vue'

  const goTo = (route:string) => {
    router.push({name:route})
  }

</script>

<style lang="scss" scoped> 

  @use "@/scss/mixings";


  footer {
    @include mixings.flexbox(column, space-between, center);
    .nav-footer {
      display: grid;
      align-content: center;
      width: 100%;
      height: 70px;
      background-color: var(--theme-color);
      box-shadow: 0 -1px 12px hsla(var(--hue), var(--sat), 15%, 0.15);
      transition: .4s;
      z-index: 90;
      .nav-footer__list {
        @include mixings.flexbox(row, space-around, center);
        list-style-type: none;
        &__item{
          @include mixings.flexbox(column, initial, center);
          border-bottom: 2px solid var(--theme-color);
          padding-bottom: 2px;
          &--active{
            padding: 10px;
            border-radius: 10px;
            background: #05a896;
          }
        }
      }
    }
  }
</style>
