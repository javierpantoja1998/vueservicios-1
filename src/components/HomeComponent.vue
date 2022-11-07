<template>
  <div style="margin-top: 20px">
    <h1>PAGINA PRINCIPAL</h1>
    <img src="./../assets/images/home.gif"/>
    <h2>{{saludo}}</h2>
  </div>
</template>

<script>
import ServicesEjemplo from './../services/ServicesEjemplo';

const service = new ServicesEjemplo();

export default {
    name: "HomeComponent",
    data(){
      return{
        saludo:""
      }
    },
    mounted(){
      this.saludo = service.getSaludo("Javi")
    }
}
</script>

<style scoped>
  img {
    width: 450px;
  }
</style>