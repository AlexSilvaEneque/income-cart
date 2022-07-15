<script setup>
    import ItemVue from './Item.vue';

    defineProps({
        state: Object
    })

    const emit = defineEmits(['remove-item'])

    function removeItem(id) {
        emit('remove-item', id)
    }
</script>

<template>
    <div class="income-list">
        <ItemVue v-for="data in state.income" :key="data.id" :income="data" @remove="removeItem" />
    </div>
</template>

<style scoped>
    .income-list {
        margin-top: 30px;
        padding: 15px;
    }
</style>