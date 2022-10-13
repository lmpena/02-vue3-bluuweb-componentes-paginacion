<script setup>
    defineProps(['inicio','fin','maxLength']);

    const emit = defineEmits(['AvanzarPagina','RetrocederPagina']);
</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button type="button" 
                class="btn btn-outline-primary"
                @click="emit('RetrocederPagina')"
                :disabled="inicio===0"
                >Previus</button>
        <button type="button" 
                class="btn btn-outline-primary"
                @click="emit('AvanzarPagina')"
                :disabled="fin===maxLength"
                >Next</button>
    </div> 
</template>

