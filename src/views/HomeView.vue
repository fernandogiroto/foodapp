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
          success-text="Vamos Começar!"
          name="slideunlock"
          @completed="createMenu()"/>
      </template>
    </Card>
    <Input>
      <template #icon>
        <IconSearch size="32" />
      </template>
    </Input>
    <div class="intro">
      <span class="intro__title">Mais Vendidos</span>
      <span class="intro__action">ver todos</span>
    </div>
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
      <div class="home-categories__options">
        <Card type="icon" :background="selectedCategory=='personal' ? 'var(--primary-color)' : 'var(--text-color)'" border="var(--primary-color)" @click="changeCategory('personal')">
          <template #icon>
            <IconUser  size="32" :color="'var(--theme-color)'"  />
          </template>
          <template #icon-description>
            <span class="card-icon--title">Pessoal</span>
          </template>
        </Card>
        <Card type="icon" :background="selectedCategory=='family' ? 'var(--primary-color)' : 'var(--text-color)'" border="var(--primary-color)" @click="changeCategory('family')">
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
      <Transition name="fade">
        <div class="home-categories__list"  v-show="!loadingCategoriesProducts">
          <Grid :columnsMobile="2" gap="15px">
            <Card type="item" :showImage="true" :image="index" :title="product.name" v-for="(product,index) in productsCategories">
            </Card>
          </Grid>
        </div>
      </Transition>
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
  import Grid from '../components/utils/Grid.vue'
  import Input from '../components/form/Input.vue'
  import {IconUser,IconUsersGroup,IconMoodKid,IconDog,IconSearch} from '@tabler/icons-vue'

  const isOpen = ref(false)
  const loadingCategoriesProducts = ref(false)
  const selectedCategory = ref('personal')
  const carouselRef = ref();
  const carouselConfig = {
    itemsToShow: 2.2,
    wrapAround: false,
    gap: 15,
    snapAlign: 'center',
  };

  const categoriesGrid = {
    columnsFull: 4,
    columnsLarge: 4,
    columnsTablet: 2,
    columnsMobile: 2,
  };

  const products = ref([
    {name:'Strogonof',types:'Vegan'},
    {name:'Lasanha',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
  ])

  const productsCategories = ref([
    {name:'Strogonof',types:'Vegan'},
    {name:'Lasanha',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
  ])

  const productsPersonal = ref([
    {name:'Strogonof',types:'Vegan'},
    {name:'Lasanha',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
  ])

  const productsFamily = ref([
    {name:'Pizza',types:'Vegan'},
    {name:'Feijoada',types:'Vegan'},
    {name:'Macarrão',types:'Vegan'},
    {name:'Hamburguer',types:'Vegan'},
  ])

  function createMenu() {
    setTimeout(()=>{
      router.push({name:'createMenu'})
    },1000)
  }

  function changeCategory(category:string) {
    loadingCategoriesProducts.value = true;
    selectedCategory.value = category;
    if(selectedCategory.value === 'personal'){
      productsCategories.value = productsPersonal.value;
      loadingCategoriesProducts.value = false;
    }
    if(selectedCategory.value === 'family'){
      productsCategories.value = productsFamily.value;
      loadingCategoriesProducts.value = false;
    }
  }

</script> 

<style lang="scss">

  @use '@/scss/mixings.scss';
  
  .modal-style {
    background-color: #ffffff !important;
  }

  .home-categories{
    @include mixings.flexbox(column,initial,center);
    gap: 25px;
    width: 100%;
    padding: 10px 0px 10px 0px;
    &__options{
      @include mixings.flexbox(row,initial,center);
      width: 100%;
      gap: 15px;
    }
    &__list{
      width: 100%;
    }
  }

  .intro{
    @include mixings.flexbox(row,space-between,center);
    &__title{
      font-weight: 600;
    }

  }

  .slideunlock.is-complete .slideunlock-progressbar {
    background-color: var(--quaternary-color)  !important;
  }
  .slideunlock.is-complete .slideunlock-text {
    color: var(--text-color);
    font-weight: 600;
  }

</style>