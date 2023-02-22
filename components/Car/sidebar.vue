<script setup>
const { makes } = useCar()

const model = ref({
    make: false,
    location: false,
    price: false
})
const route = useRoute()
const city = ref('')
function updateModel(field) {
    return model.value[field] = !model.value[field]
}

function onChangeLocation() {
    updateModel('location')
    if (!city.value) return
    if (!isNaN(parseInt(city.value))) {
        throw createError({
            statusCode: 400,
            message: "invalid City name"
        })
    }
    navigateTo(`/city/${city.value}/car/${route.params.make}`)
    city.value === ''
}

</script>

<template>
    <div class="shadow border w-64 mr-10 z-30 h-[190px]">
        <!-- LOCATION STARTS -->
        <div class="p-5 flex justify-between relative cursor-pointer border-b">
            <h3>Location</h3>
            <h3 @click="updateModel('location')" class="text-blue-400 capitalize">{{ route.params.city }}</h3>
            <div v-if="model.location" class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white">
                <input v-model="city" type="text" class="border p-1 rounded">
                <button @click="onChangeLocation" class="bg-blue-400 w-full mt-2 rounded text-white p-1">Apply</button>
            </div>
        </div>
        <!-- LOCATION END -->

        <!-- MAKE END -->
        <div class="p-5 flex justify-between relative cursor-pointer border-b">
            <h3>Make</h3>
            <h3 @click="updateModel('make')" class="text-blue-400 capitalize">Toyota</h3>
            <div class="absolute border shadow  left-56 p-5 top-1 -m-1 w-[600px] flex justify-between flex-wrap bg-white"
                v-if="model.make">
                <h4 v-for="make in makes" :key="make" class="w-1/3">
                    {{ make }}</h4>
            </div>
        </div>
        <!-- MAKE END -->

        <div class="p-5 flex justify-between relative cursor-pointer border-b">
            <h3>Price</h3>
            <h3 @click="updateModel('price')" class="text-blue-400 capitalize">500</h3>
        </div>
    </div>
</template>