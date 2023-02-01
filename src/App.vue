<template>
  <div class=" flex container h-screen w-full">
    <Navigation />
    <RouterView />  
    <Trending />
  </div>
</template>

<script setup>
import {RouterView} from 'vue-router';
import Navigation from './components/Navigation.vue';
import Trending from './components/Trending.vue';
</script>
