<template>
    <div class="container">
        

    </div>
</template>

<script>

import axios from 'axios';

export default {
    name: 'historyTimeline',
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
      .get('https://api.spacexdata.com/v3/history')
      .then(response => (this.info = response.data))
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

