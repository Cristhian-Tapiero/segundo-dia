<script setup>
defineProps(['team_info'])

</script>

<template>
    <div class="team-info-container">
        <img :src="team_info.logo" alt="Team Logo">
        <section class="team-info">
            <h1 class="team-name">{{ team_info.name }} ({{ team_info.code }})</h1>
            <h2 class="team-country">{{ team_info.country }}</h2>
            <h2 class="team-foundation">Fundado en: {{ team_info.founded }}</h2>
        </section>
    </div>
</template>
<style scoped lang="scss">
.team-info-container{
    margin-top: 1rem;
    height: 150px;
    width: 32rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: var(--gray);
    .team-info{
        display: flex;
        width: 100%;
        flex-direction: column;
        padding-right: .5rem;
        align-items: center;
        height: 80%;
        justify-content: space-between;
    }
}
</style>