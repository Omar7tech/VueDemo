<script setup lang="ts">
import { RouterView } from 'vue-router'
import Nav from './components/Nav.vue';

</script>

<template>
  <header>
    <div class="wrapper">
      <Nav />
    </div>
  </header>
  <main class="container max-w-7xl mx-auto px-4 py-8">
    <RouterView />
  </main>
</template>
