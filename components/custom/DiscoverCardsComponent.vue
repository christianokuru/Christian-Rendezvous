<script>
export default {
  props: {
    image: {
      type: String,
      required: true
    },
    text: {
      type: String,
      required: true
    }
  }
}
</script>

<template>
    <div class="relative w-[400px] h-[240px] rounded-[10px] overflow-hidden">
      <img 
        :src="image" 
        :alt="text" 
        class="w-full h-full object-cover block"
      />
      <div class="absolute inset-0 bg-black bg-opacity-50"></div>
      <div class="absolute inset-0 flex justify-center items-center text-center">
        <h3 class="font-[400] text-[24px] leading-[100%] text-[#FFFFFF]">
          {{ text }}
        </h3>
      </div>
    </div>
  </template>
  




