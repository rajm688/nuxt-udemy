<script setup>
const error = useError()
const handleIssue = () => {
    clearError({
        redirect: '/'
    })
}


</script>

<template>
    <div class="flex h-screen justify-center items-center flex-col">
        <h1 class="text-9xl">{{ error.statusCode }}</h1>
        <p class="mt-7 text-4xl">{{ error.message }}</p>
        <button class="rounded mt-7 text-2xl bg-blue-400 px-4 py-4 text-white" @click="handleIssue()">Go Back</button>
    </div>
</template>