<script setup>
const props = defineProps({ details: Object })
</script>

<template>
    <div class="mt-10">
        <NuxtImg :src="details.url" class="w-full" alt="" />
        <h1 class="mt-10 text-4xl">{{ details.name }}</h1>
        <div class="text-slate-500 flex tet-lg mt-3 border-b pb-5 justify-between">
            <div class="flex">
                <p class="mr-2">{{ details.seats }} seats</p>
                <p class="mr-2">|</p>
                <p class="mr-2">{{ details.miles }} miles</p>
            </div>
            <div class="font-bold text-2xl">$ {{ details.price }}</div>
        </div>
    </div>
</template>