<template>
<div>
    <div id="container_disks">
      <Disk
          v-for="disk,i in filteredListaDisk"
          :key="i"
          :details="disk"
      />
  </div>
</div>
 
</template>

<script>
import Disk from "./Disco.vue";
import axios from "axios";


export default {
  name: 'DischiContainer',
  props : {
    genereSelezionato : String
  },
  components: {
    Disk,
  },
  data (){
      return {
          apiUrl : "https://flynn.boolean.careers/exercises/api/array/music",
          disks : [],
          selectedGenre : ""
      }
  },
  created (){
      this.getDisks();
  },
  computed:{
    filteredListaDisk(){
      if ( this.genereSelezionato === ""){
        return this.disks
      } else if (this.genereSelezionato === "tutti") {
        return this.disks
      }

      return this.disks.filter((item)=>{
        return item.genre.includes(this.genereSelezionato)
      })
    },
    
  },
  methods : {
      getDisks(){
          axios
          .get(this.apiUrl)
          .then((result)=>{
              this.disks = result.data.response
          })
      },
  }
}
</script>


<style scoped lang="scss">
#container_disks{
    width: 70%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    flex-shrink: 1;
}
</style>