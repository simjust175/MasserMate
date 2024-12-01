<template>
  <AppBar />
  <main-display :monthly="monthly" :daysLeft="daysLeftMonth" :currencyInUse="currencyInUse"/>
</template>

<script setup>
import { ref, onMounted, watchEffect, computed } from "vue";

const monthly = ref({
  date: {},
  income: 12500,
  masser: 600
});

const daysLeftMonth = ref();
const currencyInUse = ref("ILS");
const location = ref("Paris")

const daysLeft = async () => {
  const res = await fetch(`http://localhost:3443/user/daysLeft/${location.value}`, {
    method: "GET",
    headers: {
      "Content-Type": "application/json"
    }
  });
  const { daysLeft } = await res.json();
  daysLeftMonth.value = daysLeft.daysLeft;
  console.log("fhdgsk>>", daysLeft.daysLeft);
  monthly.value.date = daysLeft.date
}

const newDay = computed(()=> new Date().getHours())
onMounted(()=>{
  daysLeft()
})
watchEffect(() => { if (newDay.value === 0) { daysLeft(); } });



</script>
