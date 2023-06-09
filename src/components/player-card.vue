<script setup>
defineProps(["player_info"])
</script>
<template>
    <div class="player-info-card">
        <img src="https://media-1.api-sports.io/football/players/154.png" alt="Leo Messi">
        <section class="info-section">
            <h1 class="player-name">{{ player_info.firstname }} {{ player_info.lastname }}</h1>
            <h2 class="player-birth">{{ player_info.birth.place }} - {{ player_info.birth.country }} ({{ (player_info.birth.date).substr(0,4) }})</h2>
            <h3 class="player-weight">{{ player_info.weight }} - {{ player_info.height }}</h3>
        </section>
    </div>
</template>
<style scoped lang="scss">
.player-info-card{
    display: flex;
    width: 32rem;
    height: 150px;
    background-color: var(--gray);
    justify-content: space-between;
    align-items: center;
    img{
        position: relative;
    }
    .info-section{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
        position: relative;
        height: 80%;
        padding-right: .5rem;
    }

}
</style>