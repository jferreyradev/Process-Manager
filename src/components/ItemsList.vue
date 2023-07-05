<script setup>
import Item from './Item.vue';

defineProps({
    data: { type: Array, required: true }
})

</script>

<template>
    <ul>
        <li v-for="item in data">
            <Item :id="item.id" :descripcion="item.descripcion" :procesos="item.procesos" />
        </li>
    </ul>
</template>

<style scoped>
    li {
        list-style: none;
    }
</style>