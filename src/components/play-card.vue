<script setup>
defineProps(["league", "teams", "goals", "time"])
</script>
<template>
    <div class="play-card-container">
        <h1 class="league-name">{{ league.name }} - {{ league.country }}</h1>
        <p class="teams-vs">{{ teams.home.name }} ({{ goals.home }}) vs {{ teams.away.name }} ({{ goals.away }})</p>
        <h2 class="time">{{ time.short }} - {{ time.elapsed }}</h2>
    </div>
</template>
<style scoped lang="scss">
.play-card-container{
    margin: 0 1rem;
    min-width: 32rem;
    min-height: 10rem;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: var(--gray);
    .league-name{
        text-align: center;
    }
}
</style>