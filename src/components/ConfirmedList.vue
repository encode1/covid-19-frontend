<template>
    <div class="card">
        <div class="card-header text-center">
            <strong>Confirmed Cases by Regions</strong>
        </div>
        <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index"
                class="list-group-item p-1">
                <button type="button"
                        class="btn btn-outline-secondary btn-block btn-sm"
                        data-toggle="button" aria-pressed="false">
                    {{region.name}} <span class="badge badge-light">{{region.confirmed}}</span>
                </button>
            </li>
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