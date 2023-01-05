<template>
  <div class="app">
    <p>
      Hello Hyrule & {{ name }} and all {{ age }} estates
    </p>
    <button @click="changeName('Zelda')">Change name</button>
    <button @click="changeAge(30)">Change Age</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components: {},
  data() {
    return {
      name: 'Link',
      age: 25 as number | string,
    }
  },
  methods: {
    changeName(name: string) {
      this.name = name;
      // return name
    },
    changeAge(age: number | string) {
      this.age = age;
      // return age
    }
  }
});
</script>

<style>

</style>
