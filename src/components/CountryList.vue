<template>
  <div class="border border-black w-1/2 mx-2 border-gray-400">
    <h2 class="text-xl font-bold py-2">Search Result</h2>
    <ul class="py-2 text-left pl-6 h-600 overflow-y-scroll">
      <li v-for="(country, key) in countryListData" :key="key" class="flex mb-2">
        <img :src="country.flag" class="w-8 mr-2" />
        <a class="cursor-pointer" @click="$emit('selected', country)"> <p>{{ country.name }}</p> </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CountryList",
  props: ["countryListData"],
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