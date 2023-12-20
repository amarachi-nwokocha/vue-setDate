
<template>
    <div class="max-w-xl mx-auto">
      <h1 class="text-3xl font-bold mb-5">Current Date: {{ currentDate }}</h1>
      <div class="flex justify-between items-center mb-5">
        <div >
          <h1 class="text-xl font-semibold py-2">Day: {{ day }}</h1>
          <button
            @click="addDays(1)"
            class=" rounded-lg px-4 py-1 bg-blue-500 text-white hover:bg-white border-2 hover:text-black hover:border-blue-500"
          >
            Add Days
          </button>
        </div>
        <div>
          <h1 class="text-xl font-semibold py-2">Month: {{ month }}</h1>
          <button
            @click="addMonths(1)"
            class=" rounded-lg px-4 py-1 bg-blue-500 text-white hover:bg-white border-2 hover:text-black hover:border-blue-500"
          >
            Add Months
          </button>
        </div>
      </div>
        <div class="ml-40">
          <button  @click="resetDate" class="bg-green-500 font-medium px-28 py-2 rounded-xl hover:shadow-2xl hover:bg-red-500 hover:font-semibold transition duration-200" >Reset</button>
        </div>
    </div>
  </template>
  
  <script>
  import { ref, computed } from "vue";
  
  export default {
    setup() {
      const currentDate = ref(new Date());
      const day = ref(currentDate.value.getDate());
      const month = ref(currentDate.value.getMonth() + 1);
  
      const updatedDate = computed(() => {
        return `${day.value}/${month.value}`;
      });
  
      const addDays = (days) => {
        currentDate.value.setDate(currentDate.value.getDate() + days);
        updateMonth();
        day.value = currentDate.value.getDate();
      };
  
      const addMonths = (months) => {
        currentDate.value.setMonth(currentDate.value.getMonth() + months);
        updateMonth();
      };
  
      const updateMonth = () => {
        month.value = currentDate.value.getMonth() + 1;
      };
      const resetDate = () => {
        currentDate.value = new Date();
        updateMonth();
        day.value = currentDate.value.getDate();
      };
  
      return {
        currentDate,
        day,
        month,
        updatedDate,
        addDays,
        addMonths,
        resetDate,
      };
    },
  };
  </script>
  
  <style>
  /* Add your styles here if needed */
  </style>
  