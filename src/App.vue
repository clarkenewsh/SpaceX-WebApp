<template>
  <div id="app">
    <header>
      <navigation />
    </header>
    <main>
      <div class="content">
        <!-- <dashboard /> -->
        <upcomingLaunches />
        <roadsterLocation />
        <StepperVertical />
      </div>
    </main>
  </div>
</template>

<script>
// import dashboard from './components/dashboard.vue' make this into a route view instead of component as this will be classed as more than a compjnent see for more structure info https://itnext.io/how-to-structure-a-vue-js-project-29e4ddc1aeeb
import navigation from './components/navigation.vue'
import upcomingLaunches from './components/upcomingLaunches.vue'
import roadsterLocation from './components/roadsterLocation.vue'
import StepperVertical from './components/historyTimeline.vue'

export default {
  name: 'App',
  components: {
    // dashboard,
    upcomingLaunches,
    navigation,
    roadsterLocation,
    StepperVertical
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: grid;
  
}

header {
  
}

main {
  
  
}
</style>
