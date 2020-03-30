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
          <div class="card-body pb-0">
            <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Confirmed</strong></h6>
            <h3 class="card-title">153</h3>
          </div>
        </div>
        <div class="card">
          <div class="card-header">
            <strong>Confirmed Cases by Regions</strong>
          </div>
          <ul class="list-group list-group-flush region-list">
            <li v-for="(region, index) in regions" :key="index" class="list-group-item">{{region.name}}</li>
          </ul>
        </div>
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
            <div class="card">
              <div class="card-header pb-0">
                <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Deaths</strong></h6>
                <h3 class="card-title mb-0">5</h3>
              </div>
              <ul class="list-group list-group-flush region-list">
                <li v-for="(region, index) in regions" :key="index" class="list-group-item">{{region.name}}</li>
              </ul>
            </div>
          </div>
          <!-- /.col-6 -->
          <div class="col-6 p-1">
            <div class="card">
              <div class="card-header pb-0">
                <h6 class="card-subtitle text-muted mb-2 small"><strong>Total Recovered</strong></h6>
                <h3 class="card-title mb-0">2</h3>
              </div>
              <ul class="list-group list-group-flush region-list">
                <li v-for="(region, index) in regions" :key="index" class="list-group-item">{{region.name}}</li>
              </ul>
            </div>
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
export default {
  name: 'HelloWorld',
  data(){
    return{
      regions: [
        {'id':1, 'name': 'Ashanti Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':2, 'name': 'Bono Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':3, 'name': 'Bono East Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':4, 'name': 'Ahafo Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':5, 'name': 'Central Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':6, 'name': 'Eastern Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':7, 'name': 'Greater Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':8, 'name': 'Northern Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':9, 'name': 'Savannah Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':10, 'name': 'North East Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':11, 'name': 'Upper East Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':12, 'name': 'Upper West Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':13, 'name': 'Volta Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':14, 'name': 'Oti Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':15, 'name': 'Western Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
        {'id':16, 'name': 'Western North Region', 'confirmed': 4, 'death': 1, 'recovered': 0, 'longitude': 0.234512, 'latitude': -0.283893},
      ]
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
