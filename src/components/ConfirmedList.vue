<template>
    <div class="card">
        <div class="card-header">
            <strong>Confirmed Cases by Regions</strong>
        </div>
        <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index" class="list-group-item">{{region.name}}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "ConfirmedList",
        props: {
            regions: Array
        }
    }
</script>

<style lang="scss" scoped>
    .region-list {
        overflow-y: scroll;
        height: 47vh;
    }
</style>