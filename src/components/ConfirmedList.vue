<template>
    <div class="card">
        <div class="card-header text-center">
            <strong>Confirmed Cases by Regions</strong>
        </div>
        <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index"
                class="list-group-item p-1">
                <button type="button"
                        @click="buttonClicked(index)"
                        :class="{active: index === activeBtn}"
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
            regions: Array,
            releaseButton: String
        },
        data() {
            return{
                activeBtn: null
            }
        },
        methods: {
            buttonClicked(index){
                if(this.activeBtn === index){
                    this.activeBtn = null;
                    this.$emit('confirmed-btn-released', index );
                }else{
                    this.activeBtn = index;
                    this.$emit('confirmed-btn-clicked', index );
                }

            }
        },
        watch: {
            releaseButton: function(val) {
                this.activeBtn = null;
                console.log(val);

            }
        }
    }
</script>

<style lang="scss" scoped>
    @media only screen and (max-width: 600px) {
        .region-list {
            overflow-y: scroll;
            height: 25vh;
        }
    }
    @media only screen and (min-width: 600px) {
        .region-list {
            overflow-y: scroll;
            height: 47vh;
        }
    }

</style>