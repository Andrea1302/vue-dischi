<template>
<div>
    <Select
      @changeSelect="changeGen" 
      :info="genres"
    />
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
import Select from "./Select.vue";

import axios from "axios";


export default {
  name: 'DischiContainer',
  components: {
    Disk,
    Select,
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
      if ( this.selectedGenre === ""){
        return this.disks
      } else if (this.selectedGenre === "tutti") {
        return this.disks
      }

      return this.disks.filter((item)=>{
        return item.genre.includes(this.selectedGenre)
      })
    },
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
      changeGen(element){
        // console.log(element);
        this.selectedGenre = element
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