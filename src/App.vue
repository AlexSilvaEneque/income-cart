<script setup>
  import { computed, reactive } from "vue";
  import FormVue from "./components/Form.vue";
  import HeaderVue from "./components/Header.vue";
  import ListVue from "./components/List.vue";

  const state = reactive({
    income: [],
    total: computed(() => {
      let temp = 0
      if (state.income.length > 0) {
        for (let i = 0; i < state.income.length; i++) {
          temp += state.income[i].value
        }
      }
      return temp
    })
  })

  function AddIncome(data) {
    let y = data.date.split("-")
    let newDate = new Date(y[0], y[1], y[2])

    state.income = [...state.income, {
      id: Date.now(),
      des: data.des,
      value: parseInt(data.value),
      date: newDate.getTime()
    }]
    console.log(state.income)
  }

  function removeItem(id) {
    state.income = state.income.filter(v => v.id != id)
  }

</script>

<template>
  <HeaderVue :total-income="state.total" />
  <FormVue @add-income="AddIncome" :state="state" />
  <ListVue :state="state" @remove-item="removeItem" />
</template>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
  }

  body {
    background: #eee;
  }
</style>