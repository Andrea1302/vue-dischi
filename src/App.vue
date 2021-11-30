<template>
  <div id="app">
    <header>
      <i class="fab fa-spotify logo"></i>
      <Select
        @changeSelect="valueGen"
        :filtro="genres"
      />
    </header>

    <main>
      <!-- qui ci sarà il componente  -->
      <DischiContainer
        :genereSelezionato="selectedGenre"
      />
    </main>
  </div>
</template>

<script>
// import fontawesome from "fontawesome"
import DischiContainer from "./components/DischiContainer.vue";
import Select from "./components/Select.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    DischiContainer,
    Select
  },
  data (){
    return {
      apiUrl : "https://flynn.boolean.careers/exercises/api/array/music",
      disks : [],
      selectedGenre : ""
    }
    
  },
  created(){
    this.getDisks()
  },
  computed : {
    genres() {
      const generi = [];
      this.disks.forEach((element)=>{
        if ( generi.includes(element.genre) === false) {
          generi.push(element.genre)
        }
      });
      return generi;
    }
  },
  methods : {
    getDisks(){
          axios
          .get(this.apiUrl)
          .then((result)=>{
              this.disks = result.data.response
          })
      },
      valueGen(elemento){
        this.selectedGenre = elemento
      }
  }
  
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body{
  background-color: #1e2d3b;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
header{
  background-color: #2e3a46;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  .logo{
    color: #1ed760;
    font-size: 40px;
    background-color: black;
    border-radius: 50%;
  }
}
main{
  // background-color: #1e2d3b;
  padding: 61px 0;
}
</style>
