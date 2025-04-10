<script setup>
import arrow from '@/assets/icons/arrow-up.svg'
defineProps({
  image: String,
  title: String,
  date: String,
  time: String,
  description: String
});
</script>

<template>
  <div class="max-w-[421px] bg-[#FFFFFF] rounded-[10px] overflow-hidden border-[1px] border-[#E0E0E0]">
    <img :src="image" alt="Event Image" class="w-full h-[240px] object-cover" />
    <div class="p-4">
      <h3 class="text-[16px] font-[600] leading-[100%] text-[#000000] mb-[4px]">
        {{ title }}
      </h3>
      <p class="text-[16px] font-[400] leading-[100%] text-[#000000] mb-[16px] mr-[8px]">
        {{ date }}<span class="text-[16px] font-[400] leading-[100%] text-[#000000]">{{ time }}</span>
      </p>
      <p class="text-[16px] font-[400] leading-[100%] text-[#000000] mb-[16px] truncate">
        {{ description }}
      </p>
      
        <nuxt-link to="/" class="flex items-center space-x-[4px]">
          <p class="text-[14px] text-[#432361] font-[500] leading-[100%] hover:underline">View details</p>
          <img :src="arrow" alt="arrow-icon">
        </nuxt-link>
    </div>
  </div>
</template>
