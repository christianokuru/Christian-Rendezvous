<script setup>
import DiscoverCardsComponent from '@/components/custom/DiscoverCardsComponent.vue'
import ButtonComponent from '@/components/custom/ButtonComponent.vue'
import pic1 from '@/assets/images/online-events.png'
import pic2 from '@/assets/images/physical-events.png'
import pic3 from '@/assets/images/hybrid-events.png'

const cards = [
    {id: 1, image: pic1, text: 'Online Events'},
    {id: 2, image: pic2, text: 'Physical Events'},
    {id: 3, image: pic3, text: 'Hybrid Events'},
]
</script>

<template>
    <section class="flex justify-between mx-[64px] pt-[127px] pb-[123px]">
        <div class="w-[393px]">
            <h1 class="font-[400] text-[32px] leading-[100%] mb-[24px] mt-[31px]">Discover a World of Events Tailored Just for You.</h1>
            <button-component text="View all events" />
        </div>

        <div class="grid grid-cols-2 gap-[25px]">
            <discover-cards-component
            v-for="card in cards"
            :key="card.id"
            :image="card.image"
            :text="card.text"
            />
        </div>
    </section>
</template>


