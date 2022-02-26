<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import { reactive, ref } from 'vue';
import Counter from './components/Counter.vue';
import Message from './components/Message.vue';

interface AppInfo {
  name: string;
  version: string;
}

const appInfo: AppInfo = reactive({
  name: 'Counter GC',
  version: '1.0.0',
})
const count = ref(0);
</script>

<template>
  <h1>TypeScript Friendly Vue 3, GC</h1>
  <a href="https://www.vuemastery.com/courses/typescript-friendly-vue3/type-safe-emit">link</a>
  <h3>{{ appInfo.name }} - {{appInfo.version}}</h3>
  <button id="b" type="button" @click="count++">simple count is: {{ count }}</button>
  
  <Counter 
    :limit="50" 
    alertMessageOnLimit="'can not go any higher'" 
  />

  <Message :msg="'Hello World'" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
#b{
  margin-bottom: 10px;
}
</style>
