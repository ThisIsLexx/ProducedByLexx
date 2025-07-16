<script setup lang="ts">

const props = defineProps<{
    titulo: string;
    descripcion: string;
}>();
</script>

<template>
    <div
        class="bg-gray-700/30 p-6 h-[320px] max-h-full rounded-lg shadow-md hover:shadow-lg hover:scale-103 hover:cursor-pointer transition-all duration-150 ease-linear">
        <h3 class="text-xl w-full flex justify-center font-semibold mb-2 text-[#00FFD1]">{{ props.titulo }}
        </h3>
        <p class="text-gray-700">{{ props.descripcion }}</p>
    </div>
</template>