<template>
  <!-- CARD DEFAULT -->
  <div class="card" v-if="type=='default'">
    <!-- <img class="card__image" :src="image" :alt="imageAlt"  v-show="showImage"/> -->
    <slot />
  </div>

  <!-- CARD ITEM -->
  <div class="card-item" v-if="type=='item'">
    <div class="card-item__background" :style="{ backgroundImage: `url('/images/marmita_${image}.png')` }"></div>
      <div class="card-item__info">
        <span class="card-item__info--title">{{ title }}</span>
        <div class="card-item__info__icons">
          <slot name="icons"></slot>
        </div>
    </div>
  </div>

  <!-- CARD ACTION -->
  <div class="card-action" v-if="type=='action'">
    <div class="card-action__intro">
      <span class="card-action__intro--subtitle">{{subtitle}}</span>
      <span class="card-action__intro--title">{{ title }}</span>
    </div>
    <slot name="action"></slot>
  </div>

  <!-- CARD ICON -->
  <div class="card-icon" v-if="type=='icon'">
    <div class="card-icon__option">
      <slot name="icon"></slot>
    </div>
    <slot name="icon-description"></slot>
  </div>
</template>
  
<script setup lang="ts">

  const props = defineProps({
    type:{type: String, default: 'default'},
    title:{type: String},
    subtitle:{type: String},
    border: { type: String, default: '1px solid #000'},
    borderRadius: {type: String, default: '8px'},
    width: {type: String, default: '100%'},
    background: {type: String, default: 'var(--primary-color)'},
    showImage:{type: Boolean, default: false},
    image:{type: Number},
    imageAlt:{type: String, default: 'Trapezist SEO'},
  });
  
</script>
  
<style lang="scss">

  @use '@/scss/mixings.scss';

  .card {
    padding: 16px;
    width: v-bind(width);
    border: v-bind(border);
    background-color: v-bind(background);
    border-radius: v-bind(borderRadius);
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    transition: box-shadow 0.3s ease;
    &__image{
      width: 100%;
    }
  }

  .card-icon {
    @include mixings.flexbox(column,center,center);
    gap: 10px;
    width: 100%;
    &__option{
      @include mixings.flexbox(row,center,center);
      padding: 5px;
      width: v-bind(width);
      height: 65px;
      border: v-bind(border);
      background-color: v-bind(background);
      border-radius: v-bind(borderRadius);
      transition: box-shadow 0.3s ease;
    }
    &--title{
      font-size: 15px;
      color: #a2a2a2;
    }
    &__active{
      width: 100%;
    }
  }

  .card-item {
    display: flex;
    flex-direction: column;
    gap: 10px;
    width: v-bind(width);
    &__background{
      padding: 16px;
      border-radius: 15px;
      height: 120px;
      background-color: v-bind(background);
      width: v-bind(width);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
      transition: box-shadow 0.3s ease;
      background-position: top center;
      background-size: cover;
    }
    &__info{
      display: flex;
      flex-direction: column;
      gap: 8px;
      &__icons{
        display: flex;
        flex-direction: row;
        gap: 5px;
      }
      &--title{
        font-size: 18px;
        font-weight: 600;
      }
    }
  }

  .card-action {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 16px;
    width: v-bind(width);
    height: auto;
    background-color:#00A896;
    border-radius: v-bind(borderRadius);
    &__intro{
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding-bottom: 30px;
      &--title{
        font-size: 32px;
        font-weight: 700;
        color: #ffffff;
      }
      &--subtitle{
        font-size: 22px;
        color: #ffffff;
      }
    }
  }
  

</style>
