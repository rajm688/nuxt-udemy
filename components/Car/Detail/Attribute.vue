<script setup>
const props = defineProps({ features: Object })
</script>

<template>
    <div class="mr-10 mt-5 boarder-b pb-5">
        <div class="flex text-lg mt-2" v-for="feature in features" :key="feature">
            <p class="rounded text-lime-800 mr-3">✔</p>
            <p>{{ feature }}</p>
        </div>
    </div>
</template>