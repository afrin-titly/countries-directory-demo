<template>
  <div class="block">
    <h1 class="text-4xl my-6">Countries Directory</h1>
    <div class="block sm:w-3/4 w-full mx-auto">
      <form @submit.prevent="submitForm">
        <input
          class="border border-black w-2/3 py-2 px-4 rounded bg-gray-300"
          type="text"
          v-model="keyword"
          placeholder="Enter country name,code,currency etc."
          @input="submitForm"
        />
        <button
          class="bg-indigo-500 mx-4 py-2 px-4 rounded text-white font-bold"
        >
          <i class="fas fa-search"></i> Search
        </button>
      </form>
      <!-- <div class="flex sm:w-3/4 w-full mx-auto"> -->
      <label
        class="items-center mt-4 mr-3"
        v-for="(region, index) in regionList"
        :key="index"
      >
        <input
          type="checkbox"
          class="form-checkbox mt-3 h-4 w-4 text-gray-600"
          :value="region"
          v-model="regionChecked"
          @change="checkRegion()"
        /><span class="ml-1 text-gray-700">{{ region }}</span>
      </label>
      <!-- </div> -->
    </div>
    <div class="flex sm:w-3/4 w-full mx-auto my-6 sm:px-10 px-1 py-4">
      <CountryList
        :countryListData="showCountryList"
        @selected="selectCountry"
        :type="resultType"
      />
      <CountryDetails v-if="countryList" :country="selectedCountryDetails" />
    </div>
  </div>
</template>

<script>
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
      countryList: [],
      selectedCountryDetails: [],
      showCountryList: [],
      resultType: "country",
      regionList: [],
      regionChecked: []
    }
  },
  created(){
    this.regionList = ['Asia', 'Africa', 'Europe', 'Americas', 'Oceania']
  },
  mounted() {
    this.fetchCountryList()
  },
  methods: {
    submitForm() {
      if(this.resultType == "country"){
        this.showCountryList = this.countryList.filter(country =>{ 
        return country.name.substring(0,this.keyword.length).toLowerCase() == this.keyword.toLowerCase()
        })
        if(this.showCountryList.length == 0){
          this.resultType = "capital"
        }
      }
      if(this.resultType == "capital"){
        this.showCountryList = this.countryList.filter(country =>{ 
        return country.capital.substring(0,this.keyword.length).toLowerCase() == this.keyword.toLowerCase()
      })
      if(this.showCountryList.length == 0){
          this.resultType = "currency"
        }
      }
      if(this.resultType=="currency"){
        this.showCountryList = this.countryList.filter(country =>{ 
        return country.currencies[0].name.substring(0,this.keyword.length).toLowerCase() == this.keyword.toLowerCase()
      })
      if(this.showCountryList.length == 0){
          this.resultType = "country"
        }
      }
      if(this.keyword==""){
        this.resultType = "country"
      }
    },
    async fetchCountryList() {
      this.showCountryList = this.countryList = await this.$axios
        .get("https://restcountries.eu/rest/v2/all")
        .then((response) => {
          return response.data;
        })
        .catch((error) => {
          console.log(error);
        });
        this.selectedCountryDetails = this.showCountryList[18]
    },
    selectCountry(country) {
      this.selectedCountryDetails = country
    },
    checkRegion() {
      this.showCountryList = this.countryList.filter(country =>{ 
        return this.regionChecked.includes(country.region) == true
    })
    if(this.showCountryList.length == 0)
    {
      this.showCountryList = this.countryList
    }
    }
  }
}
</script>