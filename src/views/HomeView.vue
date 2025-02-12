<template>
  <div class="container"> 
    <Card
      type="action"
      title="20% desconto"
      subtitle="Menu da semana com">
      <template #action>
        <slide-unlock
        ref="vueslideunlock"
        :auto-width="true"
        :circle="true"
        :width="100"
        :height="35"
        text="Criar menu da semana"
        success-text="Vamos Começar"
        name="slideunlock"
        @completed="createMenu()"/>
      </template>
    </Card>
    <Input>
      <template #icon>
        <IconSearch size="32" />
      </template>
    </Input>
    <Carousel ref="carouselRef" v-bind="carouselConfig">
      <Slide v-for="(product,index) in products" :key="product" @click="isOpen = true">
        <Card type="item" :showImage="true" :image="index" :title="product.name" >
          <template #icons>
            <img src="@/assets/images/icons/health.png" width="22px">
          </template>
        </Card>
      </Slide>
    </Carousel>

    <div class="home-categories">
      <Card type="icon" background="var(--primary-color)" border="var(--primary-color)">
        <template #icon>
          <IconUser  size="32" :color="'var(--theme-color)'"  />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Pessoal</span>
        </template>
      </Card>
      <Card type="icon" background="var(--text-color)">
        <template #icon>
          <IconUsersGroup size="32" :color="'var(--theme-color)'" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Família</span>
        </template>
      </Card>
      <Card type="icon" background="var(--text-color)">
        <template #icon>
          <IconMoodKid size="32" :color="'var(--theme-color)'" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Infantil</span>
        </template>
      </Card>
      <Card type="icon" background="var(--text-color)">
        <template #icon>
          <IconDog size="32" :color="'var(--theme-color)'" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Pet</span>
        </template>
      </Card>
    </div>
    <SwipeModal
      v-model="isOpen"
      snapPoint="300px">
      <button @click="isOpen = false">Close modal</button>
      Modal content
    </SwipeModal>
  </div>
</template>

<script setup lang="ts">

  import { ref } from 'vue';
  import router from '@/router';
  import 'vue3-carousel/carousel.css'
  import { Carousel, Slide } from 'vue3-carousel'
  import SlideUnlock from "@j2only/slide-unlock"
  import { SwipeModal } from "@takuma-ru/vue-swipe-modal"
  import Card from '../components/ui/Card.vue'
  import Input from '../components/form/Input.vue'
  import {IconUser,IconUsersGroup,IconMoodKid,IconDog,IconSearch} from '@tabler/icons-vue'

  const isOpen = ref(false)
  const carouselConfig = {
    itemsToShow: 2.2,
    wrapAround: false,
    gap: 15,
    snapAlign: 'center',
  };

  function createMenu() {
    setTimeout(()=>{
      router.push({name:'createMenu'})
    },1000)
  }

  const carouselRef = ref();

  const products = ref([
    {name:'Strogonof',types:'Vegan'},
    {name:'Lasanha',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
  ])


</script>

<style lang="scss">

  @use '@/scss/mixings.scss';
  
  .modal-style {
    background-color: #ffffff !important;
  }

  .home-categories{
    @include mixings.flexbox(row,initial,center);
    gap: 15px;
    width: 100%;
  }


</style>