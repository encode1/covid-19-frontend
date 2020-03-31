<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Coronavirus COVID-19 Ghana Cases</h1>
      </div>
      <!-- /.col-12 -->
    </div>
    <!-- /.row -->
    <div class="row">
      <div class="col-2 p-1">
        <div class="card mb-2">
          <div class="card-body text-center pb-0">
            <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Confirmed</strong></h6>
            <h3 class="card-title">152</h3>
          </div>
        </div>
        <ConfirmedList :regions="confirmed_list"/>
      </div>
      <!-- /.col-2 -->
      <div class="col-7 p-1">
        <div class="card">
          <div class="card-body">
            This is where the map will appear.
          </div>
        </div>
      </div>
      <!-- /.col-7 -->
      <div class="col-3">
        <div class="row">
          <div class="col-6 p-1">
            <DeathList :regions="death_list"/>
          </div>
          <!-- /.col-6 -->
          <div class="col-6 p-1">
            <RecoveredList :regions="recovered_list"/>
          </div>
          <!-- /.col-6 -->
        </div>
        <!-- /.row -->
      </div>
      <!-- /.col-3 -->
    </div>
    <!-- /.row -->
  </div>
  <!-- /.container -->
</template>

<script>
  import ConfirmedList from "./ConfirmedList";
  import DeathList from "./DeathList";
  import RecoveredList from "./RecoveredList";
  export default {
    name: 'Container',
    components: {
      ConfirmedList,
      DeathList,
      RecoveredList
    },
    mounted() {
      this.confirmed_list = [...this.regions];
      this.confirmed_list.sort(this.sortByProperty('confirmed')).reverse();
      this.death_list = [...this.regions];
      this.death_list.sort(this.sortByProperty('death')).reverse();
      this.recovered_list = [...this.regions];
      this.recovered_list.sort(this.sortByProperty('recovered')).reverse();
    },
    methods: {
      sortByProperty(property){
        return function(a,b){
          if(a[property] > b[property])
            return 1;
          else if(a[property] < b[property])
            return -1;

          return 0;
        }
      }
    },
    data(){
      return{
        regions: [
          {'id':1, 'name': 'Ashanti Region', 'confirmed': 8, 'death': 2, 'recovered': 1, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':2, 'name': 'Bono Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':3, 'name': 'Bono East Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':4, 'name': 'Ahafo Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':5, 'name': 'Central Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':6, 'name': 'Eastern Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':7, 'name': 'Greater Accra Region', 'confirmed': 126, 'death': 3, 'recovered': 1, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':8, 'name': 'Northern Region', 'confirmed': 10, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':9, 'name': 'Savannah Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':10, 'name': 'North East Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':11, 'name': 'Upper East Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':12, 'name': 'Upper West Region', 'confirmed': 1, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':13, 'name': 'Volta Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':14, 'name': 'Oti Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':15, 'name': 'Western Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
          {'id':16, 'name': 'Western North Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        ],
        confirmed_list: [],
        death_list: [],
        recovered_list: [],
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .region-list {
    overflow-y: scroll;
    height: 60vh;
  }
</style>
