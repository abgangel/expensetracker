<template>
  
  <div class="container">
    <Header/>
    <Balance :total="total"/>
    <IncomeExpenses/>
    <TransactionList :transactions="transactions" />
    <AddTransaction/>
  </div>
</template>
<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import { computed, ref } from 'vue';
const transactions = ref([
    { id: 1, text: 'Efectivo', amount: -400 },
    { id: 2, text: 'Pago', amount: 8000 },
    { id: 3, text: 'Efectivo', amount: -400 },
    { id: 4, text: 'Pago', amount: 8000 },
    { id: 5, text: 'Osito de peluche', amount: -850 },
    { id: 6, text: 'Vestido', amount: -3000},
]);
const total = computed(()=> {
  return transactions.value.reduce((acc, transaction)=>{
    return acc + transaction.amount;
  }, 0);
  });
</script>