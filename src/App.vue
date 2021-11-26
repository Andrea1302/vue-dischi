<template>
  <div id="app">
    <header>
      <i class="fab fa-spotify logo"></i>
    </header>

    <main>
      <!-- qui ci sarà il componente  -->
    </main>
  </div>
</template>

<script>
// import fontawesome from "fontawesome"

export default {
  name: 'App',
  components: {
  }
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
header{
  background-color: rgb(59, 58, 58);
  padding: 10px 5px;
}
.logo{
  color: #1ed760;
  font-size: 40px;
  background-color: black;
  border-radius: 50%;
}
</style>
