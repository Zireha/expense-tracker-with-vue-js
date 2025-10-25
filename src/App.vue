<script>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import AddTransaction from "./components/AddTransaction.vue";

export default {
    components: {
        Header,
        Balance,
        IncomeExpense,
        TransactionList,
        AddTransaction,
    },
};
</script>

<template>
    <div class="main-container flex justify-center p-12 bg-sky-950">
        <div class="bg-white p-14 rounded-xl w-5/6">
            <Header />
            <div
                class="container mt-4 shadow-lg py-6 bg-amber-400 flex-col align-middle rounded-md"
            >
                <Balance />
            </div>
            <div class="container pt-8">
                <IncomeExpense />
            </div>
            <div class="container pt-4">
                <TransactionList />
            </div>
            <div class="container pt-6">
                <AddTransaction />
            </div>
        </div>
    </div>
</template>

<style scoped></style>
