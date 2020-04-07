<template>
    <div class="card">
        <div class="card-body">
            <div class="row map">
                <l-map ref="map" :zoom="zoom" :center="center">
                    <l-tile-layer :url="url" :attribution="attribution" />
                    <div v-for="(region, index) in regions" :key="index">
                        <l-circle
                                v-if="region.confirmed"
                                :lat-lng="[region.latitude, region.longitude]"
                                :radius="1000 + 100 * region.confirmed"
                                :color="color"
                                :fillColor="fillColor"
                                :fillOpacity="0.7"
                        >
                            <l-popup>
                                <div>
                                    <h5>{{region.name}}</h5>
                                    <p>
                                        <strong>Confirmed:</strong> {{region.confirmed}} <br>
                                        <strong>Deaths:</strong> {{region.death}} <br>
                                        <strong>Recovered:</strong> {{region.recovered}} <br>
                                        <strong>Active:</strong> {{region.confirmed - region.recovered - region.death}}
                                    </p>
                                </div>
                            </l-popup>
                        </l-circle>
                    </div>
                </l-map>
            </div>
        </div>
    </div>

</template>

<script>
    import { Icon } from 'leaflet';

    delete Icon.Default.prototype._getIconUrl;
    Icon.Default.mergeOptions({
        iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
        iconUrl: require('leaflet/dist/images/marker-icon.png'),
        shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
    });
    import L from 'leaflet';
    import { LMap, LTileLayer, LCircle, LPopup } from 'vue2-leaflet';
    export default {
        name: "CaseMap",
        props: {
            regions: Array,
            activeRegion: Object,
        },
        components: {
            LMap,
            LTileLayer,
            LCircle,
            LPopup,
        },
        data() {
            return{
                zoom:7,
                center: L.latLng(8.126130, -1.137881),
                url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
                attribution:
                    '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
                color: 'red',
                fillColor: '#f03',
            }
        },
        watch: {
            activeRegion: function (obj){
                if (obj===null) {
                    this.closePopup(obj);
                }else {
                    this.openPopup(obj);
                }

            }
        },
        methods:{
            openPopup(obj){
                this.$refs.map.mapObject.openPopup(L.popup()
                    .setLatLng([obj.latitude, obj.longitude])
                    .setContent(
                        `<div>
                            <h5>${obj.name}</h5>
                             <p>
                                <strong>Confirmed:</strong> ${obj.confirmed} <br>
                                <strong>Deaths:</strong> ${obj.death} <br>
                                <strong>Recovered:</strong> ${obj.recovered} <br>
                                <strong>Active:</strong> ${obj.confirmed - obj.recovered - obj.death}
                             </p>
                        </div>`
                    ));
            },
            closePopup(){
                this.$refs.map.mapObject.closePopup();
            }
        }
    }
</script>

<style scoped>
    @media only screen and (max-width: 600px) {
        .map{
            height: 50vh;
        }
    }
    @media only screen and (min-width: 992px) {
        .map{
            height: 80vh;
        }
    }

</style>