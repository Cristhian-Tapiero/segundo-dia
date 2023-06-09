<script setup>
import { ref } from 'vue'
let teams = ref([])
const url = 'https://api-football-v1.p.rapidapi.com/v3/teams?search=tolima';
const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'ffb077ba4amshff7bea3c8800c8cp143f7bjsnb8a18823bb93',
		'X-RapidAPI-Host': 'api-football-v1.p.rapidapi.com'
	}
};
const mapData = (data, arr) =>{
    data.forEach(team =>{
        arr.value.push({
            name: team.team.name,
            code: team.team.code,
            country: team.team.country,
            foundation: team.team.founded,
            logo: team.team.logo
        })
    })
}

fetch(url, options)
.then(res => res.json())
.then(data =>{
    mapData(data.response, teams)
})    
.catch(err => console.log('Error de tipo ' + err))
</script>
<template>
    <div class="search-teams-container">
        <div class="team-info-container" v-for="team in teams">
            <img :src="team.logo" alt="Team logo">
            <h1 class="team-name">{{ team.name }}</h1>
            <span class="team-foundation">{{ team.foundation }}</span>
            <h2 class="team-short">{{ team.code }}</h2>
            <h2 class="team-country">{{ team.country }}</h2>
        
        </div>
    </div>
</template>