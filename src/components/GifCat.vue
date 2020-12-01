<template>
<div class="container text-center">
  <h1 class="pt-3">Obtiene tu GifCat!</h1>
  <div class="logo">
    <img alt="gatologo" src="../assets/gato logo.jpg">
  </div>
  <div class="row">
    <form class="m-auto text-light col-12 col-sm-12 col-md-12 col-lg-6 col-xl-6" @submit.prevent="obtenerGifCat">
      <div class="form-group">
        <label for="exampleFormControlInput1">Título</label>
        <input type="text" class="form-control" id="exampleFormControlInput1" v-model="titulo">
      </div>
      <div class="form-group">
        <label for="exampleFormControlSelect1">Filtro</label>
        <select class="form-control" id="exampleFormControlSelect1" v-model="filtro">
          <option value="blur">Blur</option>
          <option value="mono">Mono</option>
          <option value="sepia">Sepia</option>
          <option value="negative">Negative</option>
          <option value="paint">Paint</option>
        </select>
      </div>
      <div class="form-group">
        <label for="exampleFormControlSelect1">Color</label>
        <select class="form-control" id="exampleFormControlSelect1" v-model="color.background">
          <option value="red">Red</option>
          <option value="blue">Blue</option>
          <option value="yellow">Yellow</option>
          <option value="green">Green</option>
          <option value="orange">Orange</option>
        </select>
        <br>
        <div class="muestra text-center m-auto" :style="color"></div>
      </div>
      <div class="form-group">
        <label for="exampleFormControlInput1">Tamaño</label>
        <input type="text" class="form-control" id="exampleFormControlInput1" v-model="tamano">
      </div>
      <button type="submit">Generar GifCat</button>
    </form>
    <div class="col-12 col-sm-12 col-md-12 col-lg-6 col-xl-6" :class="resultado">
        <img :src="link" alt="" />
    </div>
  </div>
  
</div>
</template>

<script>
export default {
  name: 'GifCat',
  props: {
    cats: {
      type: Array,
      required: true,
    }
  },
  data (){
    return{
      titulo: "",
      filtro: "",
      tamano: "",
      link: "",
      color: {
        background: "",
      }
    }
  },
   methods: {
    obtenerGifCat() {
      let titulo = this.titulo;
      let filtro = this.filtro;
      let color = this.color;
      let tamano = this.tamano;
      this.link = `https://cataas.com/cat/gif/says/${titulo}?filter=${filtro}&color=${color.background}&size=${tamano}`
    },
  },
}
</script>

<style scoped>
  .logo img{
    width: 180px;
    border: 3px solid palevioletred;
    border-radius: 100%;
    margin: 20px 0;
  }

  form{
    width: 300px;
  }

  .muestra{
    width: 25px;
    height: 25px;
    border: 1px solid black;
    border-radius: 100%;
  }

  button{
    background-color: palevioletred;
    padding: 10px 30px;
    color: white;
    outline: none;
    margin-bottom: 20px;
  }

  .resultado img{
    width: 500px;
    height: 500px;
    vertical-align: middle;
  }
</style>
