<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";
import { ref, computed } from "vue";

const transactionRecords = ref([
    { id: 1, text: "Buy Chicken Noodle", amount: -10000 },
    { id: 2, text: "Sold an Item", amount: 20000 },
    { id: 3, text: "Paycheck", amount: 600000 },
    { id: 4, text: "Groceries", amount: -34000 },
]);

// get total balance
const total = computed(() => {
    return transactionRecords.value.reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0);
});

//get incomes
const income = computed(() => {
    return transactionRecords.value
      .filter((transaction) => transaction.amount > 0)
      .reduce((acc, transaction) => {
        return acc + transaction.amount;
    }, 0);
});

//get expenses
const expense = computed(() => {
    return transactionRecords.value
      .filter((transaction) => transaction.amount < 0)
      .reduce((acc, transaction) => {
        return (acc + transaction.amount)* (-1);
    }, 0);
});

</script>

<template>
    <div class="main-container flex justify-center p-12 bg-sky-950">
        <div class="bg-white p-14 rounded-xl w-5/6">
            <Header />
            <div
                class="container mt-4 shadow-lg py-6 bg-blue-950 text-white flex-col align-middle rounded-md"
            >
                <Balance :total="total" />
            </div>
            <div class="container pt-8">
                <IncomeExpense :income="income" :expenses="expense"/>
            </div>
            <div class="container pt-4">
                <TransactionList :transactions="transactionRecords" />
            </div>
            <div class="container pt-6">
                <AddTransaction />
            </div>
        </div>
    </div>
</template>
