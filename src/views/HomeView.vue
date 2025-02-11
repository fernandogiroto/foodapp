<template>
  <div class="container"> 
    <!-- <div class="home-intro">
      <h1 class="title">Delicious food</h1>
      <h1 class="title">for you</h1>
    </div> -->
    <Card
      type="action"
      title="up to 50%"
      subtitle="Get special discount">
      <template #action>
        <slide-unlock
        ref="vueslideunlock"
        :auto-width="true"
        :circle="true"
        :width="100"
        :height="35"
        text="Criar meu menu"
        success-text="success"
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
      <Slide v-for="image in images" :key="image.id" @click="isOpen = true">
        <Card type="item" :showImage="true" image="@/assets/images/plate.png" title="Strogonof" >
          <template #icons>
            <img src="@/assets/images/icons/health.png" width="22px">
          </template>
        </Card>
      </Slide>
    </Carousel>

    <div class="home-categories">
      <Card type="icon" background="#FF9F0D" border="#FF9F0D">
        <template #icon>
          <IconUser color="white" size="32" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Pessoal</span>
        </template>
      </Card>
      <Card type="icon">
        <template #icon>
          <IconUsersGroup size="32" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Família</span>
        </template>
      </Card>
      <Card type="icon">
        <template #icon>
          <IconMoodKid size="32" />
        </template>
        <template #icon-description>
          <span class="card-icon--title">Infantil</span>
        </template>
      </Card>
      <Card type="icon">
        <template #icon>
          <IconDog size="32" />
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

  const images = Array.from({ length: 10 }, (_, index) => ({
    id: index + 1,
    url: `https://picsum.photos/800/600?random=${index + 1}`,
  }));



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