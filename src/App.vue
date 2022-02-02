<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Michael Parisi Portfolio</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by type</button>
        <button @click="handleClick('type')">Order by type</button>
        <button @click="handleClick('id')">Order by id</button>
      </div>
    </header>

    <Grid :items="items" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import ItemStruct from '@/types/ItemStruct'
import OrderTermStruct from '@/types/OrderTermStruct'
import Grid from '@/components/Grid.vue'

export default defineComponent({
  name: 'App',
  components: { Grid },
  setup() {
    const items = ref<ItemStruct[]>([
      { title: 'farm worker', type: 'drawing', image: '', description: '', id: 0 },
      { title: 'quarryman', type: 'drawing', image: '', description: '', id: 0 },
      { title: 'flute player', type: 'drawing', image: '', description: '', id: 0 },
      { title: 'fisherman', type: 'drawing', image: '', description: '', id: 0 },
      { title: 'prison guard', type: 'drawing', image: '', description: '', id: 0 }
    ])
    const order = ref<OrderTermStruct>('title')

    const handleClick = (term: OrderTermStruct) => {
      order.value = term
    }

    return { items, order, handleClick }
  }
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
