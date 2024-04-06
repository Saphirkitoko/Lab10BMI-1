<script setup>
import {ref} from "vue";

import BodyMassIndex from './components/BodyMassIndex.vue'
const bmi =ref(0)
const heightEntered = ref(0)

const calculateBMI = (height) => {
  alert('todo- do math! height is' + height)
  heightEntered.value = height
  bmi.value = height // todo actually do math
}

</script>

<template>
  <div>
    <!-- Displaying the app's name-->
    <h1>{{BodyMassIndex}}</h1>
    <!-- Including theBodyMassIndex components-->
    <BodyMassIndex :metricUnits="metricUnits"@stat-entered="calculateBMI"/>
    <!-- Displaying the calculated BMI-->
    <div v-if="bmi !==null">
      <p>Your Body Mass Index(BMI)is: {{bmi.toFixed(2)}}</p>
    </div>
    <!--selecting Units-->

  <div>
  <label>Select Units:</label>
  <Select v-model="metricUnits">
    <option value="true">Metric</option>
    <option value="false">American</option>

  </Select>
  </div>
  </div>
</template>
<script>
import BodyMassIndex from './components/BodyMassIndex.vue';
import bodyMassIndex from "./components/BodyMassIndex.vue";
export default {
  components:{
    bodyMassIndex,
  },
  data(){
    return{
      appName:'BodyMassIndex calculator',
      bmi:null,
      metricUnits:true, // Default to metric units


    };

  },
methods:{
  // Methods to calculate BMI based on entered stats
  calculateBMI(stats){
    const {height, weight,bmi}= stats;
    this.bmi = bmi;
  },
  },
};
</script>



<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

