<script setup>
import { ref } from 'vue';

defineProps({
    id: { type: Number, required: true },
    descripcion: String,
    procesos: Array,
    procedimiento: String,
})

const mostrar = ref(false);

function handleMostrar() {
    mostrar.value = !mostrar.value;
}

</script>

<template>
    <div class="box">
        <div class="block">
            <p class="flex-item">{{ id }} - {{ descripcion }}</p>
            <button v-if="procesos" class="flex-item" @click="handleMostrar"> ... </button>
        </div>
        <div v-if="mostrar" class="subbox" v-for="item in procesos">
            <Item :id="item.id" :descripcion="item.descripcion" :procedimiento="item.procedimiento" />
            <input type="checkbox" name="checkProc" id="idproc" >
        </div>
    </div>
</template>

<style scoped>
.box {
    display: flex;
    flex-direction: column;
    align-content: space-between;
    padding: 10px;
    margin-bottom: 5px;
    background-color: darkgray;
    color: black;
}

.subbox {
    display: flex;
    flex-direction: column;
    align-content: space-between;
    padding: 5px;
    margin: 5px;
    border: 2px solid rgb(61, 61, 56);
}

.block {
    display: flex;
}

.flex-item {
    padding-right: 5px;
    text-align: center;
}</style>