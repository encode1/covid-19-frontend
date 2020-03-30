<template>
    <div class="card">
        <div class="card-header pb-0">
            <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Recovered</strong></h6>
            <h3 class="card-title mb-0">2</h3>
        </div>
        <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index" class="list-group-item">{{region.name}}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "RecoveredList",
        props: {
            regions: Array
        }
    }
</script>

<style lang="scss" scoped>
    .region-list {
        overflow-y: scroll;
        height: 60vh;
    }
</style>