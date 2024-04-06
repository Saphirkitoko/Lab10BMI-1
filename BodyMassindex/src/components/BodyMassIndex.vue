<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
 <div>
   <!--Displaying the app's Name-->
   <h2>Body Mass Index calculator</h2>
   <!-- Form for entering height and weight-->
   <form @submit.prevent="calculateBMI">
   <div>
     <!--Labels and inputs for height-->
     <label v-if="metricUnits">Height(meters):</label>
     <label v-else>Height (Inches):</label>
     <input type="number" v-model="Height" required>

   </div>


  <div>
    <!--Labels and inputs for weight-->
    <label v-if="metricUnits">Weight(kg):</label>
    <label v-else>Weight (lbs):</label>
    <input type="number" v-model="weight" required>
  </div>
  <!-- button to calculate BMI-->
  <button type="submit">calculate</button>
  </form>
 </div>
</template>
<script>
export default {
  data(){
return{
  height:null,
  weight:null,
};
  },
  props:{
    metricUnits:Boolean,
  },
  methods:{
    // Methods to calculate BMI and emits stats entered event
    calculateBMI(){
      const bmi =this.metricUnits
      ?this.weight/(this.height*this.height)//metric calculation
      :(this.weight/(this.height*this.height))*730;//American units calculation
      // Emitting stats-entered event with height, weight, and calculated BMI
      this.semit('stats-entered',{height:this.height,weight:this.weight,bmi});

    },
  },
};
</script>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
