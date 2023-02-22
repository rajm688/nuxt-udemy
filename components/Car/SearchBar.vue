<script setup>
const city = ref('')
const router = useRouter()
const cityError = ref(false)
const handleSearch = () => {
    if (city.value === '') {
        return cityError.value = true
    }
    navigateTo(`/city/${city.value}/car`)
}
</script>

<template>
    <div
        class="font-serif w-[1000px] test-2xl rounded-full bg-white flex justify-between overflow-hidden drop-shadow-2xl mx-auto">
        <input placeholder="search by city..." type="text" v-model="city"
            class="py-3 px-5 w-full text-2xl rounded-full focus:outline-none"
            :class="cityError ? 'border-red-500 border' : ''" />
        <button class="bg-sky-500 px-10 text-white" @click="handleSearch">Search</button>
    </div>
</template>