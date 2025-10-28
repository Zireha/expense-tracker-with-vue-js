<template>
    <h2 class="font-semibold text-3xl">Add Transaction</h2>
    <form id="form" @submit.prevent="onSubmit">
        <div class="pt-8 pb-8">
            <div class="input-container pb-4">
                <h3 class="font-bold text-lg">Expense/Income Text</h3>
                <input
                    placeholder="Enter title..."
                    type="text"
                    v-model="text"
                    class="bg-slate-200 rounded-lg w-full h-12 p-4 active:border border-slate-700 text-lg"
                />
            </div>

            <div class="input-container">
                <h3 class="font-bold text-lg">
                    Amount (Number input, add "-" for expenses)
                </h3>
                <input
                    placeholder="Enter Amount..."
                    type="number"
                    v-model="amount"
                    class="bg-slate-200 rounded-lg w-full h-12 p-4 active:border border-slate-700 text-lg"
                />
            </div>
        </div>

        <button
            class="w-full bg-slate-500 p-4 rounded-md text-white font-semibold hover:bg-slate-600"
        >
            <p>Add Transaction</p>
        </button>
    </form>
</template>

<script setup>
import { ref, useAttrs } from "vue";
import { useToast } from "vue-toastification";

const text = ref("");
const amount = ref("");
const toast = useToast();

const emit = defineEmits(["transactionSubmited"]);

const onSubmit = () => {
    if (!text.value || !amount.value) {
        toast.error("Both fields must be filled");
        return;
    }

    //do something here
    const transactionData = {
        text: text.value,
        amount: parseFloat(amount.value),
    };

    emit("transactionSubmitted", transactionData);
    //end of something statement here

    //clear the fields
    text.value = "";
    amount.value = "";
};
</script>
