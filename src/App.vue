<template>
  <div class="bg-info">
    <GifCat :cats="gif"/>
  </div>
</template>

<script>
import GifCat from './components/GifCat.vue'

export default {
  name: 'App',
  data(){
    return {
      gif:[]
    }
  },

  components: {
    GifCat
  },

   created() {
    fetch('https://cataas.com/cat/gif/')
    .then(captura => captura.json())
    .then(data =>{
      console.log(data);
      this.gif = data;
    })
    .catch(error => console.error(error));
  },
}
</script>

<style>

</style>
