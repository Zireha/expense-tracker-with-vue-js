<template>
    <div class="flex flex-col gap-4 min-h-full items-center md:flex-row">
        <div
            class="flex-col shadow-md p-4 text-center border w-full md:w-1/2 border-transparent rounded-md bg-green-300"
        >
            <h3>Income</h3>
            <p class="font-bold text-lg md:text-xl text-green-950">
                + Rp{{ income.toLocaleString("id-ID") }}
            </p>
        </div>
        <div
            class="flex-col shadow-md p-4 text-center border w-full md:w-1/2 border-transparent rounded-md bg-red-200"
        >
            <h3>Expense</h3>
            <p class="font-bold text-lg md:text-xl text-red-950">
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
