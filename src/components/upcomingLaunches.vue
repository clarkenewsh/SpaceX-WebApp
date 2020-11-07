
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

// Dealing with Errors
// There are times when we might not get the data we need from the API. There are several reasons that our axios call might fail, including but not limited to:

// The API is down.
// The request was made incorrectly.
// The API isn’t giving us the information in the format that we anticipated.
// When making this request, we should be checking for just such circumstances, and giving ourselves information in every case so we know how to handle the problem. In an axios call, we’ll do so by using catch.

// axios
//   .get('https://api.coindesk.com/v1/bpi/currentprice.json')
//   .then(response => (this.info = response.data.bpi))
//   .catch(error => console.log(error))


// This will let us know if something failed during the API request, but what if the data is mangled or the API is down? Right now the user will just see nothing. We might want to build a loader for this case, and then tell the user if we’re not able to get the data at all.

// new Vue({
//   el: '#app',
//   data () {
//     return {
//       info: null,
//       loading: true,
//       errored: false
//     }
//   },
//   filters: {
//     currencydecimal (value) {
//       return value.toFixed(2)
//     }
//   },
//   mounted () {
//     axios
//       .get('https://api.coindesk.com/v1/bpi/currentprice.json')
//       .then(response => {
//         this.info = response.data.bpi
//       })
//       .catch(error => {
//         console.log(error)
//         this.errored = true
//       })
//       .finally(() => this.loading = false)
//   }
// })
// <div id="app">
//   <h1>Bitcoin Price Index</h1>

//   <section v-if="errored">
//     <p>We're sorry, we're not able to retrieve this information at the moment, please try back later</p>
//   </section>

//   <section v-else>
//     <div v-if="loading">Loading...</div>

//     <div
//       v-else
//       v-for="currency in info"
//       class="currency"
//     >
//       {{ currency.description }}:
//       <span class="lighten">
//         <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
//       </span>
//     </div>

//   </section>
// </div>
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
