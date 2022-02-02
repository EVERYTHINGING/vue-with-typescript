<template>
    <div class="item">
        <p>{{ item.title }}</p>
        <p>{{ item.description }}</p>
        <p>{{ item.type }}</p>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType, computed } from 'vue'
import ItemStruct from '@/types/ItemStruct'

export default defineComponent({
  name: "Item",
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  setup(props) {
    return {  }
  },
})
</script>

<style scoped>
.item {
    border: solid 2px #000;
}
</style>