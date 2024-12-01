<template>
  <v-container class="fill-height fill-width bg-grey-lighten-2 pa-6" fluid>
    <v-responsive class="fill-height fill-width bg-red=lighten-3" width="100%">
      <v-row class="pb-4">
        <carousal height="100" />
      </v-row>

      <v-row class="d-flex fill-width">
        <number-card  :currency="currency" :monthly="monthly" :daysLeft="daysLeft"
        :monthlyPercnt="monthlyPercent" :chodesh="dateConverter"/>
        <!-- <number-card info="given" :currency="currency" :monthly="monthly" :daysLeft="daysLeft"
        :monthlyPercnt="monthlyPercent" /> -->
      </v-row>

      <v-row>

        <v-col cols="md-6 xs-12">
          <main-form /> 
        </v-col>

        <v-col cols="md-6 xs-12">
          <div>
             <progress-bar color="blue" label="Monthly goal" :percentage="monthlyPercent" :daysLeft="daysLeft"
            :masserGiven="props.monthly.masser" :masserToGive="props.monthly.income" :currency="currency" />
          </div>
          <!-- <div class="mt-4">
            <progress-circle :percent="monthlyPercent" />
          </div> -->
          <div class="mt-5">
            <SparklinesDashboard />
          </div>         
        </v-col>

      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup>
// import BarDashboard from './BarDashboard.vue';
// import ProgressCircle from './ProgressCircle.vue';
import MainForm from "../MainDisplay/MainInput/MainForm.vue"
import NumberCard from './NumberCard.vue';
import SparklinesDashboard from './SparklinesDashboard.vue';
import { defineProps, computed } from "vue";
import MainFormVue from './MainInput/MainForm.vue';



const props = defineProps({
  currencyInUse: String,
  monthly: Object,
  daysLeft: Number
})
console.log(props.monthly.date);


const monthlyPercent = computed(() => (Math.round(props.monthly.masser / (props.monthly.income / 10) * 100)))
const currency = computed(() => {
  switch (props.currencyInUse) {
    case "EUR":
      return "€"
    case "GBP":
      return "£"
    case "ILS":
      return "₪"
    case "FRANC":
      return "₣"
    default: "$"
      break;
  }
})

const dateConverter = computed(() => {
  switch (props.monthly.date.mm) {
    case 1:
      return { en: "Nissan", he: "ניסן" };
    case 2:
      return { en: "Iyar", he: "אייר" };
    case 3:
      return { en: "Sivan", he: "סיון" };
    case 4:
      return { en: "Tammuz", he: "תמוז" };
    case 5:
      return { en: "Av", he: "אב" };
    case 6:
      return { en: "Elul", he: "אלול" };
    case 7:
      return { en: "Tishrei", he: "תשרי" };
    case 8:
      return { en: "Cheshvan", he: "חשון" };
    case 9:
      return { en: "Kislev", he: "כסלו" };
    case 10:
      return { en: "Tevet", he: "טבת" };
    case 11:
      return { en: "Shevat", he: "שבט" };
    case 12:
      return { en: "Adar", he: "אדר" }; // ~~~~~ ADD A OPTION IF ADAR ALEF!!! ~~~~~~~//
    case 13:
      return { en: "Adar II", he: "'אדר ב" };
    default:
      return { en: "Unknown", he: "לא ידוע" };
  }
});

</script>

<style></style>