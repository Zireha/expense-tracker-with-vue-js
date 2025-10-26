<template>
<div class="flex justify-between gap-12 mx-auto">
    <div class="flex-col shadow-md p-4 text-center border w-1/2 border-transparent rounded-md bg-green-300">
        <h3>Income</h3>
        <p class="font-bold text-lg text-green-950">+ Rp{{ income.toLocaleString("id-ID") }}</p>
    </div>
    <div class="flex-col shadow-md p-4 text-center border w-1/2 border-transparent rounded-md bg-red-200">
        <h3>Expense</h3>
        <p class="font-bold text-lg text-red-950">- Rp{{ expenses.toLocaleString("id-ID") }}</p>
    </div>
</div>
</template>

<script setup>

import { defineProps } from 'vue';

const props = defineProps({
  income: {
    type: Number,
    required: true
  },
  expenses: {
    type: Number,
    required: true
  }
})

</script>