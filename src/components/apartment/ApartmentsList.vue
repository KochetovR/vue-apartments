<template>
    <Container>
        <div class="apartments-list">
            <ApartmentsItem 
                v-for="{id, descr, rating, price, imgUrl} in items"
                :key="id"
                :descr="descr"
                :rating="rating"
                :price="price"
                :imgUrl="imgUrl"
                class="apartments-list__item"
            />
        </div>
    </Container>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import Container from '../shared/Container.vue'
import ApartmentsItem from './ApartmentsItem.vue'
import apartmentTypes from '../../types/IApartments'
export default defineComponent({
    name: 'ApartmentsList',
    components: {
        Container,
        ApartmentsItem
    },
    props: {
        items: {
            type: Array as PropType<apartmentTypes[]>
        }
    },
})
</script>

<style scoped lang="scss">
.apartments-list {
  display: flex;
  flex-wrap: wrap;
  margin-left: -15px;
  margin-right: -15px;
  &__item {
    margin-bottom: 30px;
  }
}

// 
.apartments-item {
  position: relative;
  width: 33.333%;
  padding: 0 15px;
  margin-bottom: 30px;
  &__inner {
    position: relative;
  }
  &__content {
    position: relative;
    padding: 20px;
    opacity: 0;
    transition: opacity 0.4s;
    background: rgba(#0f1d2d, 0.7);
    min-height: 200px;
    color: #fff;
    text-align: left;
    line-height: 1.4;
    cursor: pointer;
    z-index: 1;
    &:hover {
      opacity: 1;
    }
  }
  &__description {
    margin-bottom: 20px;
    max-height: calc(1em * 1.4 * 3);
    overflow: hidden;
  }
  &__rating {
    margin-bottom: 20px;
  }
  &__price {
    font-size: 20px;
    font-weight: 600;
  }
  &__photo {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

</style>