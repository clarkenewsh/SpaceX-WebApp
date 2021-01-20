
<template>
    <nav>
        <a href="">SpaceX API Data Dashboard</a>
    </nav>

    
  
</template>

<script>
export default {
  name: 'navigation',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

nav {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: black;
  height: 80px;
  font-family: 'Space Mono', monospace;
  
}

nav a {
  color: white;
}

</style>
