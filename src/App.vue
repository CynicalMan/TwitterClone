<template>
  <div class=" flex container h-screen w-full">
    <Navigation />
    <RouterView />    
  </div>
</template>

<script setup>
import {RouterView} from 'vue-router';
import Navigation from './components/Navigation.vue';
</script>
