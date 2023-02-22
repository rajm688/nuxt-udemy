<script setup>
const route = useRoute()
const { cars } = useCar()
const { toTitleCase } = useUtilities()

const car = computed(() => {
    return cars.find(car => car.id === parseInt(route.params.id))
})
if (!car.value) {
    throw createError({
        statusCode: 404,
        message: `Car with id ${route.params.id} does not exist`
    })
}

useHead({
    title: `${toTitleCase(route.params.name)}`
})
definePageMeta({
    layout: 'custom',

})
</script>

<template>
    <div v-if="car">
        <CarDetailHero :details="car" />
        <CarDetailAttribute :features="car.features" />
        <CarDetailDescription :desc="car.description" />
        <CarDetailContact />
    </div>
</template>