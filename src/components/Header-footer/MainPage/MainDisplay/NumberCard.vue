<template>
    <div class="col-md-12 col-xl-4">
        <div class="card mb-3 widget-content bg-midnight-bloom">
            <div class="widget-content-wrapper text-white">
                <div class="widget-content-left">
                    <div class="widget-heading">Total Masser</div>
                    <div class="widget-subheading">For Chodesh {{ props.chodesh.en }}</div>
                </div>
                <div class="widget-content-right">
                    <div class="widget-numbers text-white"><span>{{ props.currency }}{{ props.monthly.income }}</span></div>
                </div>
            </div>
        </div>
    </div>
    <div class="col-md-12 col-xl-4">
        <div class="card mb-3 widget-content bg-arielle-smile">
            <div class="widget-content-wrapper text-white">
                <div class="widget-content-left">
                    <div class="widget-heading">Total gave</div>
                    <div class="widget-subheading">Total Clients Profit</div>
                </div>
                <div class="widget-content-right">
                    <div class="widget-numbers text-white"><span>{{ props.currency }}{{ props.monthly.masser }}</span></div>
                </div>
            </div>
        </div>
    </div>
    <div class="col-md-12 col-xl-4">
        <div class="card mb-3 widget-content bg-grow-early">
            <div class="widget-content-wrapper text-white">
                <div class="widget-content-left">
                    <div class="widget-heading">Avarage daily</div>
                    <div class="widget-subheading">People Interested</div>
                </div>
                <div class="widget-content-right">
                    <div class="widget-numbers text-white"><span>{{ props.currency }} {{ averageDailyCalculator }}</span></div>
                </div>
            </div>
        </div>
        </div>
</template>


<script setup>
import { computed, defineProps } from "vue";

const props = defineProps({
    monthly: Object,
    chodesh: String,
    currency: String,
    daysLeft: Number,
    monthlyPercent: Number
})

const leftOverCalc = (props.monthly.income / 10) - props.monthly.masser;
const stillToGive = computed(() => (leftOverCalc))
const averageDailyCalculator = computed(() => leftOverCalc / props.daysLeft)



</script>

<style></style>


<!-- <v-card class="elevation-3 d-flex flex-column align-start justify-space-evenly pa-4" :class="infoColor" height="100"
width="300">

<div class="text-grey-darken-1 d-flex justify-space-between d-flex" v-if="props.info === 'income'">
    <div class="d-flex flex-column">
        <div class="text-grey-lighten-1">Monthly income</div>
        <div class="text-grey-lighten-4">Masser based on Your income</div>
    </div>
    <div class="text-lg-h2">{{ props.currency }}{{ props.monthly.income }}</div>
</div>

<div class="text-grey-darken-1 d-flex justify-space-between d-flex" v-else-if="props.info === 'given'">
    <div class="d-flex flex-column">
        <div class="text-grey-lighten-1">Masser given</div>
        <div class="text-grey-lighten-4">Masser based on Your income</div>
    </div>
    <div class="text-h4 text-bold">{{ props.currency }}{{ props.monthly.masser }} || {{ monthlyPercent }}%</div>
</div>

<div lass="text-grey-darken-1 d-flex justify-space-between d-flex" v-else>
    Left over: <span class="text-green">{{ props.currency }} {{ stillToGive }}</span> Average daily: <span
        class="text-green">{{ props.currency }} {{ averageDailyCalculator }}</span>
</div>
</v-card> -->

<!--  const infoColor = computed(() => {
    //     switch (props.info) {
    //         case "income":
    //             return "bg-midnight-bloom"
    //             break;
    //         case "given":
    //             return "bg-blue-lighten-1"
    //             break;
    
    //         default:
    //             return "bg-green-lighten-1"
    //             break;
    //     }
    // }) -->