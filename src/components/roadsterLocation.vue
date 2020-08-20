<template>
    <div class="container">
        <h2>Roadster Locator</h2>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">Target</th>
                    <th scope="col">Speed (mph)</th>
                    <th scope="col">Distance from Earth(mi)</th>
                    <th scope="col">Distance from Mars(mi)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">{{info.name}}</th>
                    <td>{{info.speed_mph}}</td>
                    <td>{{info.earth_distance_mi}}</td>
                    <td>{{info.mars_distance_mi}}</td>
                    <!-- <div v-for="images in info" v-bind:key="images.flickr_images">
                       <img :src="info.flickr_images" alt="">
                    </div> -->

                    
               </tr>
            </tbody>
        </table>

    </div>
</template>

<script>

import axios from 'axios';

export default {
    name: 'roadsterLocation',
    props: {
        msg: String
    },
    data () {
      return {
        info: null,
      }
    },

  // Axios Api request
  mounted () {
    axios
      .get('https://api.spacexdata.com/v3/roadster')
      .then(response => (this.info = response.data))
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>