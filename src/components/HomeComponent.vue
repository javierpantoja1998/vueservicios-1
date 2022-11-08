<template>

  <div style="margin-top: 20px">
    <h1>PAGINA PRINCIPAL</h1>
    <img src="./../assets/logo.png"/>
    <h2 style="color: blue">{{saludo}}</h2>
  </div>
</template>

<script>
import ServiceEjemplo from './../services/ServiceEjemplo';
//PARA PODER UTILIZAR NUESTROS SERVICIO, DEBEMOS INSTANCIAR UN OBJETO DE LA CLASE EN EL COMPONENTE
const service = new ServiceEjemplo();

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