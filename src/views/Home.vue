<template>
  <div class="block">
    <h1 class="text-4xl my-6"> Countries Directory </h1>
    <div class="block w-1/2 mx-auto">
      <form @submit.prevent="submitForm">
        <input class="border border-black w-2/3 py-2 px-4 rounded bg-gray-300" type="text" v-model="keyword" placeholder="Enter country name,code,currency etc.">
        <button class="bg-indigo-500 mx-4 py-2 px-4 rounded text-white font-bold"><i class="fas fa-search"></i> Search</button>
      </form>
    </div>
    <div class="flex w-1/2 mx-auto my-6 px-10 py-4">
      <CountryList />
      <CountryDetails />
    </div>
  </div>
  
</template>

<script>
// @ is an alias to /src
import CountryList from '../components/CountryList.vue'
import CountryDetails from '../components/CountryDetails.vue'
export default {
  name: 'Home',
  components: {
    CountryDetails,
    CountryList
  },
  data(){
    return {
      keyword: '',
    }
  },
  methods: {
    submitForm() {
      console.log(this.keyword)
    }
  }
}
</script>
