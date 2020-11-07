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

</style>