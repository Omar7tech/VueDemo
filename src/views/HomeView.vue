<script setup lang="ts">
import Card from '@/components/Card.vue';
</script>

<template>
  <div v-for="i in 10" :key="i" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
    <Card :key="i" />
  </div>
</template>
