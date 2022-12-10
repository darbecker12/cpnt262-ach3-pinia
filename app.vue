<script setup lang="ts">
import { storeToRefs, mapActions} from "pinia";
import {useCounterStore} from "./store/useCounter"

const main = useCounterStore();

const {counter, name } = storeToRefs(main);

const { addOne } = main;

function add(value: number) {
  main.$patch(state => { state.counter += value
  });
}

function reset() {
  main.$reset();
}
</script>
<template>
  <div>
    <h3>Hello</h3>
    <h4>{{ counter}}</h4>
    <button @click="add(15)">Click me</button>
    <button @click="reset">Reset</button>
  </div>
</template>

<style>
#app {
  font-family: Avenir,Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
