<script setup>
    defineProps({ totalIncome: Number })
</script>

<template>
    <header>
        <h1>Income Tracker</h1>
        <div class="total-income">S/ {{ totalIncome }}</div>
    </header>    
</template>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 15px 30px;
        background-color: #313131;
        border-bottom: 5px solid #ffce00;
    }

    header h1 {
        color: #eee;
        font-size: 28px;
    }

    .total-income {
        border-radius: 15px;
        background: #ffce00;
        box-shadow: inset 0px 0px 6px rgba(0, 0, 0, 0.25);
        color: #fff;
        font-weight: 700;
        font-size: 20px;
        padding: 8px 30px;
        text-align: center;
        text-shadow: 0px 3px 3px rgba(0, 0, 0, 0.25);
    }
</style>