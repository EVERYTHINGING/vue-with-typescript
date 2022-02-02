<template>
  <div class="grid">
    <p>Ordered by {{ order }}</p>
    <template v-for="item in orderedItems" :key="item.id">
      <Item :item="item" />
    </template>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from 'vue'
import ItemStruct from '@/types/ItemStruct'
import OrderTermStruct from '@/types/OrderTermStruct'
import Item from '@/components/Item.vue'

export default defineComponent({
  name: 'Grid',
  components: { Item },
  props: {
    items: {
      type: Array as PropType<ItemStruct[]>,
      required: true
    },
    order: {
      type: String as PropType<OrderTermStruct>,
      required: true
    }
  },
  setup(props) {
    const orderedItems = computed(() => {
      return [...props.items].sort((a: ItemStruct, b: ItemStruct) => {
        return a[props.order] > b[props.order] ? 1 : -1
      })
    })

    return { orderedItems }
  },
})
</script>

<style scoped>
  .grid {
    max-width: 960px;
    margin: 40px auto;
  }
  .grid ul {
    padding: 0
  }
  .grid li {
    list-style-type: none;
    background: white;
    padding: 16px;
    margin: 16px 0;
    border-radius: 4px;
  }
  .grid h2 {
    margin: 0 0 10px;
    text-transform: capitalize;
  }
  .salary {
    display: flex;
  }
  .salary img {
    width: 30px;
  }
  .salary p {
    color: #17bf66;
    font-weight: bold;
    margin: 10px 4px;
  }
  .list-move {
    transition: all 1s;
  }
</style>