<template>
    <div class="card">
        <div class="card-header text-center pb-0">
            <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Deaths</strong></h6>
            <h3 class="card-title mb-0">5</h3>
        </div>
        <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index" class="list-group-item p-1">
                <button type="button"
                        @click="buttonClicked(index)"
                        :class="{active: index === activeBtn}"
                        class="btn btn-outline-secondary btn-block btn-sm"
                        data-toggle="button" aria-pressed="false">
                    {{region.name}} <span class="badge badge-light">{{region.death}}</span>
                </button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "DeathList",
        props: {
            regions: Array,
            releaseButton: String
        },
        data() {
            return{
                activeBtn: null,

            }
        },
        methods: {
            buttonClicked(index){
                if(this.activeBtn === index){
                    this.activeBtn = null;
                    this.$emit('death-btn-released', index );
                }else{
                    this.activeBtn = index;
                    this.$emit('death-btn-clicked', index );
                }

            },
        },
        watch: {
            releaseButton: function(val) {
                console.log(val);
                if(val) {
                    this.activeBtn = null;
                }

            }
        }
    }
</script>

<style lang="scss" scoped>
    .region-list {
        overflow-y: scroll;
        height: 60vh;
    }
</style>