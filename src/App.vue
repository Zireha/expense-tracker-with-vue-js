<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import IncomeExpense from "./components/IncomeExpense.vue";
import AddTransaction from "./components/AddTransaction.vue";
import TransactionList from "./components/TransactionList.vue";

import { ref, computed, onMounted } from "vue";
import { useToast } from "vue-toastification";

const toast = useToast();
const transactionRecords = ref([]);
onMounted(() => {
    const savedTransaction = JSON.parse(
        localStorage.getItem("transactionRecords"),
    );
    if (savedTransaction) {
        transactionRecords.value = savedTransaction;
    }
});

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
    const total = transactionRecords.value
        .filter((transaction) => transaction.amount < 0)
        .reduce((acc, transaction) => {
            return acc + transaction.amount;
        }, 0);

    return total == 0 ? 0 : total * -1;
});

//add transaction
const handleTransactionSubmitted = (transactionData) => {
    transactionRecords.value.push({
        id: uniqueIdGenerator(),
        text: transactionData.text,
        amount: transactionData.amount,
        date: new Date().toLocaleDateString()
    });

    saveTransactionRecordToLocalStorage();
    toast.success("Transaction Added");
};

//delete transaction
const handleTransactionDeleted = (id) => {
    transactionRecords.value = transactionRecords.value.filter(
        (transaction) => transaction.id !== id,
    );
    saveTransactionRecordToLocalStorage();
    toast.success("Transaction Deleted!");
};

//id generator
const uniqueIdGenerator = () => {
    return Math.floor(Math.random() * 1000000);
};

//save to local storage
const saveTransactionRecordToLocalStorage = () => {
    localStorage.setItem(
        "transactionRecords",
        JSON.stringify(transactionRecords.value),
    );
};

</script>

<template>
    <main>
        <div
            id="main-container"
            class="flex items-start justify-center p-12 bg-sky-950 min-h-screen"
        >
            <div
                class="flex flex-col bg-white p-14 rounded-xl max-w-7xl lg:w-full gap-8"
            >
                <Header />
                <div
                    class="shadow-lg py-6 bg-blue-950 text-white flex-col align-middle rounded-md"
                >
                    <Balance :total="total" />
                </div>
                <div>
                    <IncomeExpense :income="income" :expenses="expense" />
                </div>
                <div>
                    <TransactionList
                        :transactions="transactionRecords"
                        @transactionDeleted="handleTransactionDeleted"
                    />
                </div>
                <div>
                    <AddTransaction
                        @transactionSubmitted="handleTransactionSubmitted"
                    />
                </div>
            </div>
        </div>
    </main>
</template>
