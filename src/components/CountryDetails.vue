<template>
    <div class="border border-black w-1/2 sm:mx-2 mx-0 border-gray-400">
        <h2 class="text-xl font-bold py-2">Country Details</h2>
        <img class="w-36 mx-auto my-4" :src="country.flag" alt="">
        <p class="text-xl font-bold">{{country.name}}</p>
        <ul>
            <li>Capital: <span class="font-bold">{{country.capital}}</span></li>
            <li>Population: <span class="font-bold">{{country.population}}</span></li>
            <li>Area: <span class="font-bold">{{country.area}}</span></li>
            <li>Population: <span class="font-bold">{{country.population}}</span></li>
            <li>Language: <span class="font-bold">{{country.languages ? country.languages.slice(0,1)[0].name: ""}}</span></li>
            <li>Currency: <span class="font-bold">{{country.currencies ? country.currencies[0].code : "" }}</span></li>
            <li>Region: <span class="font-bold">{{country.region}}</span></li>
            <li>Timezone: <span class="font-bold">{{country.timezones ? country.timezones[0] : "" }}</span></li>
            
            
        </ul>
        
    </div>
</template>

<script>
    export default {
        name: "CountryDetails",
        props: ["country"],
    }
</script>

<style scoped>

</style>