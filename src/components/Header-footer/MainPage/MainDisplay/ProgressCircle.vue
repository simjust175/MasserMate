<template>
  <v-card class="text-center bg-grey-lighten-3 d-flex justify-space-evenly">
    <v-progress-circular model-value="85" :rotate="360" :size="120" :width="15" color="green-darken-2">
      <template v-slot:default> 85 % </template>
    </v-progress-circular>
    <v-progress-circular :model-value="props.percent" :rotate="360" :size="120" :width="15" :color="percentageColor" auto-draw>
      <template v-slot:default> {{ props.percent }} % </template>
    </v-progress-circular>
  </v-card>
</template>

<script setup>
import { defineProps, computed } from "vue"


const props = defineProps({
  percent: Number
})

const percentageColor = computed(()=>{
    if (props.percent > 50) {
        return "green"   
    }
    else if(props.percent < 50 && props.percentage > 25){
        return "yellow"
    } else {
        return "orange"
    }
})


</script>

<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>