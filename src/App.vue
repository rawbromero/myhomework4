<script setup>
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import {ref, computed} from 'vue'
import AddTransaction from './components/AddTransaction.vue';


const tranasctions = ref([
    {id: 1, Text: 'Paycheck', amount: 700.00},
    {id: 1, Text: 'Water Bill', amount: -72.83},
    {id: 1, Text: 'Electric Bill', amount: -153.89},
    {id: 1, Text: 'Return Item', amount: 20.00},
  

  ])

  const sum = computed(()=>{
      return tranasctions.value.reduce((acc, x)=>{
        return acc+x.amount

      },0)

  })



  const moneyIn = computed(()=>{
      return tranasctions.value
      .filter((x)=>x.amount>0)
      .reduce((acc, x)=>{
        return acc+x.amount

      },0)

  })

  const moneyOut = computed(()=>{
      return tranasctions.value
      .filter((x)=>x.amount<0)
      .reduce((acc, x)=>{
        return acc+x.amount

      },0)

  })



      </script>








<template>
<Header></Header>
<div class="container">
  <Balance :total="sum"></Balance>
  <IncomeExpense :income="moneyIn" :expense ="moneyOut"></IncomeExpense>
  <AddTransaction></AddTransaction>

</div>


</template>