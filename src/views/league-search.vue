<script setup>
import { ref } from 'vue'

let leagues = ref([])

const url = `https://api-football-v1.p.rapidapi.com/v3/leagues?id=39`;

const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'ffb077ba4amshff7bea3c8800c8cp143f7bjsnb8a18823bb93',
		'X-RapidAPI-Host': 'api-football-v1.p.rapidapi.com'
	}
}

fetch(url, options)
.then(res => res.json())
.then(data => {
    mapData(data.response, leagues)
})
.catch(err => console.log('Error de tipo: ' + err))

const mapData = (data, arr) =>{
    data.forEach(league => {
        arr.value.push({
            name: league.league.name,
            logo: league.league.logo,
            country: league.country.name,
            country_flag: league.country.flag
        })
    })
}
</script>

<template>
    <div class="leagues-container">
        <div class="league-info" v-for="league in leagues">
            <h1 class="league-name">{{ league.name }}</h1>
            <img :src="league.logo" alt="League logo" class="league-logo">
            <h2 class="country-name">{{ league.country }}</h2>
            <img :src="league.country_flag" alt="Country flag" class="country-flag">
        
        </div>
    </div>
</template>