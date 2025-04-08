<script setup>
import heroBG from '@/assets/images/heroBg.png'
</script>

<template>
    <section class="relative bg-gray-100 h-[640px] overflow-hidden">
      <!-- Background image (optional) -->
      <img :src="heroBG" class="absolute inset-0 w-full h-full object-cover z-0" alt="Hero background" />
  
      <!-- Bottom Left Text -->
      <div class="absolute bottom-6 left-6 z-10">
        <h1 class="text-4xl font-bold text-gray-900">
          Welcome to our platform
        </h1>
        <p class="mt-2 text-lg text-gray-600 max-w-sm">
          Discover amazing features crafted just for you.
        </p>
      </div>
  
      <!-- Bottom Right Component Slot (for now just a placeholder box) -->
      <div class="absolute bottom-6 right-6 z-10">
        <!-- You can replace this with any component -->
        <div class="bg-white shadow-lg rounded-md p-6 w-[280px]">
          <h2 class="text-lg font-semibold text-gray-800 mb-2">Extra Content</h2>
          <p class="text-sm text-gray-600">This could be a call to action, image, or anything!</p>
        </div>
      </div>
    </section>
  </template>
  