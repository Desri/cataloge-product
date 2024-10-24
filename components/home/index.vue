<template>
  <div>
    <img src="@/assets/img/banner.png" class="w-full mb-1 mx-auto" alt="Banner" />

    <div class="box px-3 mb-1">
      <div class="flex align-center justify-between">
        <h2>
          Kategory
        </h2>
      </div>
      <HomeCategory />
    </div>

    <div class="box px-3 mb-1">
      <div class="flex align-center justify-between">
        <h2>
          Men's Clothing
        </h2>
        <NuxtLink to="/category/men's clothing">
          Selengkapnya
        </NuxtLink>
      </div>
      
      <div class="grid grid-cols-2 gap-4">
        <CardProductSkeleton v-if="isShowLoading" />
        <CardProduct :data-produk="dataMan" />
      </div>
    </div>

    <div class="box px-3 mb-1">
      <div class="flex align-center justify-between">
        <h2>
          Jewelery
        </h2>
        <NuxtLink to="/category/jewelery">
          Selengkapnya
        </NuxtLink>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <CardProductSkeleton v-if="isShowLoading" />
        <CardProduct :data-produk="dataJewelery" />
      </div>
    </div>

    <div class="box px-3 mb-1">
      <div class="flex align-center justify-between">
        <h2>
          Electronics
        </h2>
        <NuxtLink to="/category/electronics">
          Selengkapnya
        </NuxtLink>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <CardProductSkeleton v-if="isShowLoading" />
        <CardProduct :data-produk="dataElectronics" />
      </div>
    </div>

    <div class="box px-3 mb-1">
      <div class="flex align-center justify-between">
        <h2>
          Women's Clothing
        </h2>
        <NuxtLink to="/category/women's clothing">
          Selengkapnya
        </NuxtLink>
      </div>
      <div class="grid grid-cols-2 gap-4">
        <CardProduct :data-produk="dataWomen" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
  const isShowLoading = ref<boolean>(true)
  const dataMan = ref()
  const dataJewelery = ref()
  const dataElectronics = ref()
  const dataWomen = ref()

  const store = useProductsStore()
  const { listMan, listJewelery, listElectronics, listWomen } = storeToRefs(store)

  onMounted(async () => {
    store.getMan()
    store.getJewelery()
    store.getElectronics()
    store.getWomen()
    isShowLoading.value = false
  });

  dataMan.value = listMan
  dataJewelery.value = listJewelery
  dataElectronics.value = listElectronics
  dataWomen.value = listWomen
</script>

<style lang="scss">
  .box {
    h2 {
      font-size: 16px;
      padding-left: 8px;
      border-left: 4px solid #00be7e;
    }
    a {
      color: #5c72ff;
      font-size: 12px;
      font-weight: 600;
    }
    .shadow-box {
      box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px -1px rgba(0, 0, 0, 0.1);
      .title-skeleton {
        margin-bottom: 10px;
      }
    }
  }
</style>
