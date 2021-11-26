<template>
  <div id="container_disks">
    <disk
        v-for="disk,i in disks"
        :key="i"
        :details="disk"
    />
  </div>
</template>

<script>
import disk from "./Disco.vue";
import axios from "axios";


export default {
  name: 'DischiContainer',
  components: {
    disk,
  },
  data (){
      return {
          apiUrl : "https://flynn.boolean.careers/exercises/api/array/music",
          disks : []
      }
  },
  created (){
      this.getDisks();
  },
  methods : {
      getDisks(){
          axios
          .get(this.apiUrl)
          .then((result)=>{
              this.disks = result.data.response
              console.log(this.disks);
          })
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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