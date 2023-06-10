<script setup>
import { ref } from 'vue'
import teamCard from '../components/team-card.vue';

let teams = ref([])

const url = 'https://api-football-v1.p.rapidapi.com/v3/teams?search=chelsea';

const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'ffb077ba4amshff7bea3c8800c8cp143f7bjsnb8a18823bb93',
		'X-RapidAPI-Host': 'api-football-v1.p.rapidapi.com'
	}
}

const mapData = (data, arr) =>{
    data.forEach(team =>{
        arr.value.push(team.team)
    })
}

fetch(url, options)
.then(res => res.json())
.then(data =>{
    mapData(data.response, teams)
    console.log(data.response);
})    
.catch(err => console.log(`Error de tipo ${err}`))

</script>

<template>
    <div class="search-teams-container">
        <teamCard v-for="team in teams" :team_info="team"/>
    </div>
</template>

<style scoped lang="scss">
.search-teams-container{
    display: flex;
    width: 100vw;
    flex-direction: column;
    align-items: center;
}
</style>