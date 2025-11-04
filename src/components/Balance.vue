<template>
<div class="pl-4">
    <h3 class="text-md md:text-xl pb-2">Your Balance</h3>
    <p class="font-bold text-2xl md:text-4xl">Rp{{ total.toLocaleString("id-ID") }}</p>
</div>
</template>

<script setup>

import { defineProps } from 'vue';

const props = defineProps({
  total: {
    type: Number,
    required: true
  }
});
  
</script>