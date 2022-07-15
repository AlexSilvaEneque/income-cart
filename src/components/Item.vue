<script setup>

    const props = defineProps({
        income: Object
    })

    const emit = defineEmits(['remove'])
    
    function forDate() {
        let date = new Date(props.income.date)
        let day = date.getDate()
        let month = date.getMonth()
        let year = date.getFullYear()
        let formatteDate = day + "/" + month + "/" + year
        return formatteDate
    }

    function removeItem() {
        emit('remove', props.income.id)
    }

</script>

<template>
    <div class="income-item">
        <div class="removeItem" @click="removeItem">x</div>
        <div class="desc">{{ income.des }}</div>
        <div class="price">S/{{ income.value }}</div>
        <div class="date">{{ forDate() }}</div>
    </div>
</template>

<style scoped>
    .income-item {
        position: relative;
        display: flex;
        padding: 15px 15px 15px 0px;
        background-color: #fff;
        border-radius: 8px;
        max-width: 600px;
        margin: 0 auto 30px;
    }
    .removeItem {
        color: red;
        font-weight: 600;
        font-size: 20px;
        line-height: 1;
        text-align: center;
        margin: 0 45px;
    }
    .desc {
        color: #666;
        flex: 1 1 100%;
        font-size: 20px;
    }
    .price {
        color: #666;
        min-width: 100px;
        font-size: 20px;
    }
    .date {
        color: #666;
        text-align: right;
        font-size: 20px;
    }
</style>