<template>
  <div class="disk">
    <img :src="details.poster" :alt="details.title">
    <h2>
        {{details.title}}
    </h2>

    <span>
        {{details.author}}
    </span>

    <span>
        {{details.year}}
    </span>
  </div>

</template>

<script>
export default {
  name: 'Disk',
  props : {
      details : Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .disk{
        width: 18%;
        padding: 10px;
        background-color: #2e3a46;
        color: #756253;
        text-align: center;
        margin-bottom: 40px;
    }
    .disk h2{
        color: white;
        margin: 10px 0;
    }
    .disk img{
        max-width: 100%;
        aspect-ratio: 1;
    }
    span{
        display: block;
    }

    @media all and ( max-width:1200px ){
        .disk{
            width: 26%;
        }
    }
    @media all and ( max-width:992px ){
        .disk{
            width: 30%;
        }
    }
    @media all and ( max-width:768px ){
        .disk{
            width: 40%;
        }
    }
    @media all and ( max-width:576px ){
        .disk{
            width: 100%;
        }
    }
</style>