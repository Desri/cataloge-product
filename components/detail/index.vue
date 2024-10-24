<template>
  <div>
    <div class="box-detail">
      <img :alt="detailProduct.title" :src="detailProduct.thumbnail" class="w-full" />
      <div class="px-3">
        <h1>
          {{ detailProduct.title }}
        </h1>
        <div class="mb-1 flex align-center rating">
          <Rating /> {{ detailProduct.rating }}
        </div>
        <span>
          ${{ detailProduct.price }}
        </span>
        <p>
          {{ detailProduct.description }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { Rating } from '@/icons'
  const store = useProductsStore()
  const { detailProduct } = storeToRefs(store)
  const { slug } = useRoute().params

  await store.getDetailProduct(slug)
</script>

<style lang="scss" scoped>
  .box-detail {
    img {
      height: 180px;
      object-fit: cover;
      aspect-ratio: 1 / 1;
    }
    h1 {
      font-size: 18px;
      color: #3b3b3b;
      margin-bottom: 5px;
      text-transform: capitalize;
    }
    .rating {
      svg {
        width: 22px;
        color: #dbdb25;
        margin-right: 4px;
      }
    }
  }
</style>
