<template>
    <h3 class="pt-2 font-semibold text-3xl">History</h3>
    <div class="pt-6">
        <ul class="space-y-3">
            <li
                v-for="transaction in transactions"
                :key="transaction.id"
                class="group flex items-center bg-stone-100 rounded-lg overflow-hidden shadow-md"
            >
                <div
                    class="flex-1 flex items-center justify-between pt-4 pl-4 pb-4 pr-2 transition-all duration-300"
                >
                    <span class="text-lg font-medium">{{
                        transaction.text
                    }}</span>
                    <span class="text-lg font-semibold">
                        {{ nominalConverter(transaction.amount) }}
                    </span>
                </div>

                <div class="end-container flex items-center">
                    <div
                        class="flex w-0 opacity-0 overflow-hidden transition-all duration-300 group-hover:w-12 group-hover:opacity-100"
                    >
                        <button @click="deleteTransaction(transaction.id)" class="p-2 hover:bg-stone-200 rounded">
                            <img
                                src="\src\assets\trash-can.svg"
                                width="20"
                                color="red"
                            />
                        </button>
                    </div>

                    <div
                        id="history-label"
                        :class="
                            transaction.amount < 0
                                ? 'bg-red-600'
                                : 'bg-green-600'
                        "
                        class="text-white px-2 h-full min-h-[60px] transition-colors"
                    ></div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script setup>

import { defineProps } from 'vue';

const emit = defineEmits(['transactionDeleted'])

const props = defineProps({
  transactions: {
    type: Array,
    required: true
  }
})

const nominalConverter = (amount) =>
    amount < 0
        ? `- Rp${(amount * -1).toLocaleString("id-ID")}`
        : `Rp${amount.toLocaleString("id-ID")}`;

const deleteTransaction = (id) => {
  emit('transactionDeleted', id);
}
</script>
