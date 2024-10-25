<template>
  <Card
    v-for="(data, index) in dataProduk"
    :key="index"
    :pt="{
      body: {
        class: 'card-body'
      },
      title: 'title-product'
    }"
  >
    <template #header>
      <img :alt="data.title" :src="data.thumbnail" />
      <!-- <div>
        <Hearth />
      </div> -->
    </template>
    <template #title>
      <NuxtLink :to="`/detail/${data.id}`">
        {{ data.title }}
      </NuxtLink>
    </template>
    <template #subtitle>
      {{ data.category }}
    </template>
    <template #content>
      <p class="mb-0">
        ${{ data.price }}
      </p>
    </template>
  </Card>
</template>

<script setup lang="ts">
  // import { Hearth } from '@/icons'
  const props = defineProps({
    dataProduk: {
      type: Array,
      required: true
    },
  });
  const { dataProduk } = props
</script>

<style lang="scss">
  .p-card {
    border: 1px solid #d5d5d5;
    img {
      width: 100%;
      height: 120px;
      object-fit: cover;
      aspect-ratio: 1 / 1;
    }
  }
  .card-body {
    padding: 15px;
    .title-product {
      a {
        font-size: 15px;
        overflow: hidden;
        color: #3b3b3b;
        display: -webkit-box !important;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
      }
    }
  }
</style>
