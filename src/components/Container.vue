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
      <div class="col-lg-7 p-1 order-lg-2">
        <CaseMap :regions="regions" :activeRegion="activeRegion"/>
      </div>
      <!-- /.col-7 -->
      <div class="col-lg-2 p-1 order-lg-1">
        <div class="card mb-2">
          <div class="card-body text-center pb-0">
            <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Confirmed</strong></h6>
            <h3 class="card-title">{{confirmed_cases}}</h3>
          </div>
        </div>
        <ConfirmedList
                @confirmed-btn-clicked="confirmedBtnClicked"
                @confirmed-btn-released="confirmedBtnReleased"
                :regions="confirmed_list"
                :releaseButton="confirmBtn_release"
        />
      </div>
      <!-- /.col-2 -->
      <div class="col-lg-3 order-lg-3">
        <div class="row">
          <div class="col-6 p-1">
            <DeathList
                    @death-btn-clicked="deathBtnClicked"
                    @death-btn-released="deathBtnReleased"
                    :regions="death_list"
                    :releaseButton="deathBtn_release"
                    :death_cases="death_cases"
            />
          </div>
          <!-- /.col-6 -->
          <div class="col-6 p-1">
            <RecoveredList
                    @recovered-btn-clicked="recoveredBtnClicked"
                    @recovered-btn-released="recoveredBtnReleased"
                    :regions="recovered_list"
                    :releaseButton="recoverBtn_release"
                    :recovered_cases="recovered_cases"
            />
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
  import CaseMap from "./CaseMap";
  export default {
    name: 'Container',
    components: {
      ConfirmedList,
      DeathList,
      RecoveredList,
      CaseMap
    },
    mounted() {
      this.regions.forEach(this.addConfirmCases);
      this.regions.forEach(this.addDeathCases);
      this.regions.forEach(this.addRecoveredCases);
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
      },
      confirmedBtnClicked(index){
        this.activeRegion= this.confirmed_list[index];
        this.deathBtn_release = 'confirm' + index;
        this.recoverBtn_release = 'confirm' + index;
      },
      confirmedBtnReleased(){
        this.activeRegion= null;
      },
      deathBtnClicked(index){
        this.activeRegion= this.death_list[index];
        this.confirmBtn_release = 'death' + index;
        this.recoverBtn_release = 'death' + index;
      },
      deathBtnReleased(){
        this.activeRegion= null;
      },
      recoveredBtnClicked(index){
        this.activeRegion= this.recovered_list[index];
        this.confirmBtn_release = 'recover' + index;
        this.deathBtn_release = 'recover' + index;
      },
      recoveredBtnReleased(){
        this.activeRegion= null;
      },
      addConfirmCases(obj){
        this.confirmed_cases += obj.confirmed;
      },
      addDeathCases(obj){
        this.death_cases += obj.death;
      },
      addRecoveredCases(obj){
        this.recovered_cases += obj.recovered;
      }
    },
    data(){
      return{
        regions: [
          {'id':1, 'name': 'Ashanti Region', 'confirmed': 9, 'death': 2, 'recovered': 1, 'longitude': -1.610249, 'latitude': 6.679563},
          {'id':2, 'name': 'Bono Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -2.328566, 'latitude': 7.336451},
          {'id':3, 'name': 'Bono East Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -1.932456, 'latitude': 7.596365},
          {'id':4, 'name': 'Ahafo Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -2.513065, 'latitude': 6.804260},
          {'id':5, 'name': 'Central Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -1.116047, 'latitude': 5.497993},
          {'id':6, 'name': 'Eastern Region', 'confirmed': 1, 'death': 0, 'recovered': 0, 'longitude': -0.482580, 'latitude': 6.343303},
          {'id':7, 'name': 'Greater Accra Region', 'confirmed': 183, 'death': 3, 'recovered': 30, 'longitude': -0.181830, 'latitude': 5.608725},
          {'id':8, 'name': 'Northern Region', 'confirmed': 10, 'death': 0, 'recovered': 0, 'longitude': -0.831974, 'latitude': 9.408296},
          {'id':9, 'name': 'Savannah Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -1.821803, 'latitude': 9.108334},
          {'id':10, 'name': 'North East Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -0.372241, 'latitude': 10.520953},
          {'id':11, 'name': 'Upper East Region', 'confirmed': 1, 'death': 0, 'recovered': 0, 'longitude': -0.866108, 'latitude': 10.793896},
          {'id':12, 'name': 'Upper West Region', 'confirmed': 1, 'death': 0, 'recovered': 0, 'longitude': -1.910249, 'latitude': 10.679563},
          {'id':13, 'name': 'Volta Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.483655, 'latitude': 6.615524},
          {'id':14, 'name': 'Oti Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': 0.178542, 'latitude': 8.059044},
          {'id':15, 'name': 'Western Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -2.140560, 'latitude': 5.437483},
          {'id':16, 'name': 'Western North Region', 'confirmed': 0, 'death': 0, 'recovered': 0, 'longitude': -2.806650, 'latitude': 6.115648},
        ],
        confirmed_cases: 0,
        death_cases: 0,
        recovered_cases: 0,
        confirmed_list: [],
        death_list: [],
        recovered_list: [],
        activeRegion: null,
        confirmBtn_release: null,
        deathBtn_release: null,
        recoverBtn_release: null,

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
