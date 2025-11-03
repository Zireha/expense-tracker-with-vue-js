<template>
    <div class="flex flex-col lg:flex lg:flex-row justify-between gap-12 mx-auto">
        <div
            class="flex-col shadow-md p-4 text-center border lg:w-1/2 border-transparent rounded-md bg-green-300"
        >
            <h3>Income</h3>
            <p class="font-bold text-xl lg:text-2xl text-green-950">
                + Rp{{ income.toLocaleString("id-ID") }}
            </p>
        </div>
        <div
            class="flex-col shadow-md p-4 text-center border lg:w-1/2 border-transparent rounded-md bg-red-200"
        >
            <h3>Expense</h3>
            <p class="font-bold text-xl lg:text-2xl text-red-950">
                - Rp{{ expenses.toLocaleString("id-ID") }}
            </p>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
    income: {
        type: Number,
        required: true,
    },
    expenses: {
        type: Number,
        required: true,
    },
});
</script>
