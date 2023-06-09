<script setup>

import { ref } from 'vue';

import playerCard from '../components/player-card.vue';

let players = ref([])

const url = 'https://api-football-v1.p.rapidapi.com/v3/players?league=61&search=messi';

const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'ffb077ba4amshff7bea3c8800c8cp143f7bjsnb8a18823bb93',
		'X-RapidAPI-Host': 'api-football-v1.p.rapidapi.com'
	}
};
const mapData = (data, arr) =>{

	data.forEach(player =>{

		arr.value.push(player.player)

	})
}

fetch(url, options)
.then(res => res.json())
.then(data =>{
	console.log(data.response);
	mapData(data.response, players)
})
.catch(err => console.log('Error de tipo ' + err))

</script>
<template>
	<div class="players-results-container">
		<playerCard v-for="player in players" :player_info="player"/>
	</div>
</template>
<style scoped lang="scss">
.players-results-container{
	width:100vw;
	display: flex;
	flex-direction: column;
	align-items: center;
}
</style>