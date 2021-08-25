<template>
    <div class="border border-black w-1/2 mx-2 border-gray-400">
        <h2 class="text-xl font-bold py-2">Search Result</h2>
        <ul class="py-2 text-left pl-6">
            <li v-for="(country,key) in countryList" :key="key" class="flex mb-2">
                <img :src="country.flag" class="w-8 mr-2"> 
                <p> {{ country.name }} </p>
                
                </li>
        </ul>
        
    </div>
</template>

<script>
    export default {
        name: "CountryList",
        data() {
            return {
                countryList: []
            }
        },
        mounted() {
            this.fetchCountryList()
        },
        methods: {
            fetchCountryList() {
                this.$axios.get("https://restcountries.eu/rest/v2/all").then(response=>{
                    // console.log(response.data)
                    this.countryList = response.data
                    console.log(this.countryList[0])
                }).catch(error=>{
                    console.log(error)
                })
            }
        }
    }
</script>

<style scoped>

</style>