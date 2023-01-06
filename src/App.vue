<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order By title</button>
        <button @click="handleClick('salary')">Order By salary</button>
        <button @click="handleClick('location')">Order By location</button>
      </div>
    </header>

    <JobsList v-bind:jobs="jobs" v-bind:order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
// Have {reactive, toRefs} in here for other vue ways

import Job from './types/Job'
import JobsList from './components/JobsList.vue';
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobsList },
  setup() {
    //                         *"setup Hook" and Compisition API
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
    ])

    const order = ref<OrderTerm>('title');

    const handleClick = (term: OrderTerm) => {
      order.value = term;
      console.log(term)
    }

    return { jobs, handleClick, order }
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
</style>
