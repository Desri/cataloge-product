<template>
  <div>
    <div class="flex align-center justify-between">
      <h2>
        Kategory
      </h2>
    </div>
    <div v-if="listCategory" class="list-category">
      <ul>
        <li v-for="(data, index) in listCategory.slice(0,8)" :key="index" class="text-center mb-1">
          <NuxtLink :to="`/category/${data.slug}`">
            <div class="icon">
              <Jewellery v-if="index === 1" />
              <Bridal v-if="index === 3" />
              <Makeup v-if="data.slug === 'beauty'" class="beauty" />
            </div>
            <p>
              {{ data.name }}
            </p>
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { Jewellery, Bridal, Makeup } from '@/icons'
  const store = useProductsStore()
  const { listCategory } = storeToRefs(store)

  onMounted(async () => {
    store.getCategory()
  });
</script>

<style lang="scss">
  .list-category {
    overflow: hidden;
    ul {
      padding: 0px;
      overflow: hidden;
      li {
        float: left;
        width: 25%;
        list-style: none;
        a {
          margin: 0px;
          font-weight: normal;
          font-size: 14px;
          text-transform: capitalize;
          p {
            line-height: 13px;
            margin: 0px;
          }
          .icon {
            background: #00be7e;
            text-align: center;
            width: 50px;
            line-height: 80px;
            height: 50px;
            border-radius: 50%;
            margin: auto;
            margin-bottom: 5px;
            svg {
              width: 40px;
              height: 40px;
            }
          }
        }
        .icon {
          .beauty {
            width: 31px;
          }
        }
      }
    }
  }
</style>
