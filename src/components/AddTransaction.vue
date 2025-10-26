<template>
    <h2 class="font-semibold text-3xl">Add Transaction</h2>
    <div class="container pt-8 pb-8">
        
        <div class="input-container pb-4">
            <h3 class="font-bold text-lg">Expense/Income Text</h3>
            <input placeholder="Enter title..." type="text" class="bg-slate-200 rounded-lg w-full h-12 p-4 active:border border-slate-700 text-lg">
        </div>
        
        <div class="input-container">
            <h3 class="font-bold text-lg">Amount (Number input, add "-" for expenses)</h3>
            <input placeholder="Enter Amount..." type="number" class="bg-slate-200 rounded-lg w-full h-12 p-4 active:border border-slate-700 text-lg">
        </div>
        
    </div>
    
    <button class="w-full bg-slate-500 p-4 rounded-md text-white font-semibold hover:bg-slate-600">
        <p>Add Transaction</p>
    </button>
</template>

<script>
</script>