<script setup>
import heroBG from '@/assets/images/heroBg.png'
import SearchComponent from '@/components/custom/SearchComponent.vue'
</script>

<template>
    <section class="relative bg-gray-100 h-[640px] overflow-hidden">
      <!-- Background image (optional) -->
      <img :src="heroBG" class="absolute inset-0 w-full h-full object-cover z-0" alt="Hero background" />
  
      <!-- Bottom Left Text -->
      <div class="absolute top-[428px] left-[64px] z-10">
        <h1 class="text-[32px] font-[400] text-[#FFFFFF] leading-[100%] w-[511px]">
          Ready to Rock? Discover the Hottest Events Here – Your Calendar's New Best Friend!
        </h1>
      </div>
  
      <!-- Bottom Right Component Slot (for now just a placeholder box) -->
      <div class="absolute top-[458px] right-[84px] z-10">
        <search-component />
      </div>
    </section>
  </template>
  