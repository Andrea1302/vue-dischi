<template>
<form id="seleziona" action="">
    <select id="style_select" @change="selectOption($event)">
        <option selected disabled value=""> Seleziona un genere musicale</option>
        <option v-for="item,i in info " :key="i" :value="item.genre"> {{item.genre}} </option>
    </select>
</form>
 
</template>

<script>
export default {
  name: 'Select',
  props : {
      info : Object
  },
  data () {
      return {
          selectedOption : null
      }
  },
  methods : {
      selectOption(event){
          this.selectedOption = event.target.value
          this.$emit('changeSelect',this.selectedOption)
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #seleziona{
        display: flex;
        justify-content: center;
        margin-bottom: 20px;
    }
    #style_select{
        background-color: #2e3a46;
        color: white;
        padding: 10px;
    }
</style>