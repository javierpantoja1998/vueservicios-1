<template>
  <!-- <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
           <router-link class="nav-link" to="/coches">Coches</router-link>
        </li>
        <li class="nav-item">
           <router-link class="nav-link" to="/empleados">Empleados</router-link>
        </li>
        <li class="nav-item" v-for="ofi in oficios" :key="ofi">
           <router-link class="nav-link" :to=" '/oficios/' + ofi ">{{ofi}}</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav> -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container-fluid">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
           <router-link class="nav-link" to="/coches">Coches</router-link>
        </li>
        <li class="nav-item">
           <router-link class="nav-link" to="/empleados">Empleados</router-link>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            Oficios
          </a>
          <ul class="dropdown-menu" >
            <li v-for="ofi in oficios" :key="ofi">
                <router-link class="dropdown-item" :to=" '/oficios/' + ofi ">{{ofi}}</router-link>
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>

<script>
import axios from 'axios';
import Global from './../Global';

export default {
    name: "MenuComponent",
    data(){
        return {
            oficios: []
        }
    },
    methods: {
        loadOficios(){
            var request = "api/Empleados/oficios";
            var url = Global.urlEmpleados + request;

            axios.get(url).then(response => {
                this.oficios = response.data;
            });
        }
    },
    mounted() {
        this.loadOficios();
    }
}
</script>

<style>

</style>