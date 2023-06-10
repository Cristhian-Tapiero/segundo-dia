<script setup>
import { ref } from 'vue';

import playCardVue from '../components/play-card.vue';

let matches = ref([])

const url = 'https://api-football-v1.p.rapidapi.com/v3/fixtures?live=all';

const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'ffb077ba4amshff7bea3c8800c8cp143f7bjsnb8a18823bb93',
		'X-RapidAPI-Host': 'api-football-v1.p.rapidapi.com'
	}
};

fetch(url, options)
.then(res => res.json())
.then((data) =>{

    mapArray(data.response, matches)

})
.catch(err => console.log(err))

const mapArray = (data, arr) =>{

    data.forEach(play=>{
        arr.value.push({
            league: play.league, 
            teams: play.teams, 
            goals: play.goals,
            time: play.fixture.status
        })
    })
}

</script>

<template>
    <div class="match-playing-container">
        <div class="grid-container">
            <playCardVue v-for="match in matches" :league="match.league" :teams="match.teams" :goals="match.goals" :time="match.time"/>
        </div>
    </div>
</template>
<style scoped lang="scss">
.match-playing-container{
    max-width: 100vw;
    display: flex;
    justify-content: center;

    .grid-container{
        position: relative;
        width: 90%;
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 1rem;
    }
}
</style>