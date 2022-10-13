<script setup>
    defineProps({
        title: String,
        id: Number,
        body: {
            type: String,
            default: "Sin descripcion"
        },
        colorText: String
    });

    const emit = defineEmits(['cambiarFavoritoNombre']);
</script>

<template>
    <div class="card">
        <div class="card-body">
            <h5 class="card-title"
                :class="`text-${colorText}`"
                > {{ id }} - {{ title }} </h5>
            <p> {{ body }} </p>
            <button 
                @click="emit('cambiarFavoritoNombre', title)"
                class="btn btn-outline-primary"
            >Favorito
            </button>
        </div>        
    </div>
</template>


