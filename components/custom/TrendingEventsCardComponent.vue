<script setup>
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
      <h3 class="text-[16px] font-semibold text-[#333] mb-1">
        {{ title }}
      </h3>
      <p class="text-[14px] text-[#4F4F4F] mb-2">
        {{ date }} • {{ time }}
      </p>
      <p class="text-[14px] text-[#828282] leading-[1.5] mb-3">
        {{ description }}
      </p>
      <a href="#" class="text-[14px] text-[#2F80ED] font-medium hover:underline">
        View details →
      </a>
    </div>
  </div>
</template>
