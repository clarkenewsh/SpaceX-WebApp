<template>
  <div id="app">
    <header>
      <dashboard />
    </header>
    <main>
      <aside class="sidebar">
        <navigation />
      </aside>
      <div class="content">
        <upcomingLaunches />
      </div>
    </main>
    
    
    
  </div>
</template>

<script>
import dashboard from './components/dashboard.vue'
import navigation from './components/navigation.vue'
import upcomingLaunches from './components/upcomingLaunches.vue'

export default {
  name: 'App',
  components: {
    dashboard,
    upcomingLaunches,
    navigation
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
}
</style>
