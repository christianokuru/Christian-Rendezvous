<script setup>
import { useRoute } from 'vue-router'
import NavbarComponent from "@/components/custom/NavbarComponent.vue"
import FooterComponent from "@/components/custom/FooterComponent.vue"

const route = useRoute()

const isHeroPage = computed(() => route.path === '/') // change this if your hero is on another path

const { progress, isLoading, error, start, finish, clear } = useLoadingIndicator({
  throttle: 900,
  duration: 1000
})
</script>

<template>
  <NuxtLoadingIndicator color="#9751da" />
  <div class="relative">
    <navbar-component class="absolute top-0 left-0 right-0" />

    <div :class="isHeroPage ? '' : 'pt-[90px]'">
      <nuxt-page />
    </div>

    <footer-component />
  </div>
</template>
