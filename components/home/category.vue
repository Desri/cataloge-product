<template>
  <div>
    <div class="list-category">
      <ul>
        <li v-for="(data, index) in listCategory" :key="index" class="text-center">
          <NuxtLink to="/#">
            <div class="icon">
              <Jewellery v-if="index === 1" />
              <Bridal v-if="index === 3" />
            </div>
            {{ data }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup lang="ts">
  import { Jewellery, Bridal } from '@/icons'
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
      }
    }
  }
</style>
