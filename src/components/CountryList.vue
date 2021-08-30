<template>
  <div class="border border-black w-1/2 sm:mx-2 mx-0 border-gray-400">
    <h2 class="text-xl font-bold py-6">Search Result</h2>
    <ul class="py-2 text-left pl-2 h-600 overflow-y-scroll">
      <li v-for="(country, key) in countryListData" :key="key" class="block mb-2 sm:flex">
        <img :src="country.flag" class="w-16 h-10 mr-2" />
        <a class="cursor-pointer hover:text-blue-500 hover:underline" @click="$emit('selected', country)"> <p>{{ country.name }}<br> 
        {{type=="capital" ? country.capital : type == "currency" ? country.currencies[0].name : ""}}</p> 
         </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CountryList",
  props: ["countryListData", "type"],
  emits: ["selected"],
//   data() {
//     return {
//       countryList: [],
//     };
//   },
};
</script>

<style scoped>
</style>