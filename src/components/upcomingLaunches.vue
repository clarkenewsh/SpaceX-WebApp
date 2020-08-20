
<template>
  <section>
    
    <div class="container">
    <h2>Upcoming Launches:</h2>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Flight No</th>
          <th scope="col">Mission Name</th>
          <th scope="col">Mission Deatils</th>
          <th scope="col">Launch Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="info in info" v-bind:key="info.flight_number"> 
          <th scope="row">{{info.flight_number}}</th>
          <td>{{info.mission_name}}</td>
          <td>{{info.details}}</td>
          <td>{{info.launch_date_utc}}</td>
        </tr>
      </tbody>
    </table> 
  </div> 
  </section>
</template>

<script>
import axios from 'axios';

export default {
  name: 'upcomingLaunches',
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
      .get('https://api.spacexdata.com/v3/launches/upcoming')
      .then(response => (this.info = response.data))
  },

  // Fetch Api request 

}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
