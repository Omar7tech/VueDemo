<script setup lang="ts">
import { ref } from 'vue';
import { RouterLink } from 'vue-router';

const isMenuOpen = ref(false);

// Define your navigation items in one place
const navItems = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Demo', path: '/demo' },
];

// Define common classes to keep the template readable
const linkClasses = "px-3 py-1.5 text-sm font-medium rounded-md transition-colors text-gray-500 hover:text-gray-900 hover:bg-gray-50";
const activeClasses = "bg-gray-100 text-gray-900";
</script>

<template>
  <nav class="bg-white border-b border-gray-200 w-full">
    <div class="max-w-7xl mx-auto px-4 md:px-6">
      <div class="flex h-14 items-center justify-between">

        <div class="flex items-center gap-8">
          <RouterLink to="/" class="flex items-center font-semibold text-gray-900 tracking-tight shrink-0">
            <div class="w-7 h-7 bg-black rounded mr-2 flex items-center justify-center text-white text-xs font-bold">S
            </div>
            SYSTEM
          </RouterLink>

          <div class="hidden md:flex items-center gap-1">
            <RouterLink v-for="item in navItems" :key="item.path" :to="item.path" :class="linkClasses"
              :active-class="activeClasses">
              {{ item.name }}
            </RouterLink>
          </div>
        </div>

        <button @click="isMenuOpen = !isMenuOpen"
          class="md:hidden p-2 text-gray-500 hover:bg-gray-100 rounded-md transition-colors" aria-label="Toggle menu">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M4 6h16M4 12h16m-7 6h7" />
            <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
    </div>

    <div v-if="isMenuOpen" class="md:hidden border-t border-gray-100 bg-white px-4 py-3 space-y-1 shadow-lg">
      <RouterLink v-for="item in navItems" :key="item.path" :to="item.path" @click="isMenuOpen = false"
        class="block px-3 py-2 rounded-md text-sm font-medium transition-colors text-gray-600 hover:bg-gray-50"
        :active-class="activeClasses">
        {{ item.name }}
      </RouterLink>
    </div>
  </nav>
</template>