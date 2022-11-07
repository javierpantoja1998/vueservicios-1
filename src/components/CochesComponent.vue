<template>
<div>
    <h1>Api Coches</h1>
    <!-- <div v-for="car in coches" :key="car.idCoches">
        <h1 style="color: blue"><span style="color: black">Marca: </span> {{car.marca}}</h1>
        <h1 style="color: blue"><span style="color: black">Modelo: </span> {{car.modelo}}</h1>
        <h2 style="color: red"><span style="color: black">Conductor: </span>{{car.conductor}}</h2>
        <img :src="car.imagen" style="width: 150px; height: 150px"/>
        <hr/>
    </div> -->
    <div class="card" style="width: 18rem; margin: 0 auto; margin-bottom: 20px" v-for="car in coches" :key="car.idCoches">
        <img :src="car.imagen" class="card-img-top">
        <div class="card-body">
            <h5 class="card-title">{{car.marca}}</h5>
            <p class="card-text"><span style="color: black">Marca: </span> {{car.marca}}</p>
            <p class="card-text"><span style="color: black">Modelo: </span> {{car.modelo}}</p>
            <p class="card-text"><span style="color: black">Conductor: </span> {{car.conductor}}</p>
        </div>
    </div>
</div>
</template>

<script>
    //NECESITAMOS IMPORTAR axios y Global
    import axios from 'axios';
    import Global from './../Global';
    //AQUI PODEMOS DECLARAR VARIABLES PARA UTILIZARLAS 
    //DENTRO DE CUALQUIER METODO DEL COMPONENT
    //var urlApi = "https://apicochespaco.azurewebsites.net/";

    export default {
        name: 'CochesComponent',
        data(){
            return {
                coches: []
            }
        },
        methods: {
            loadCoches() {
                var request = "webresources/coches";
                var url = Global.urlCoches + request;

                axios.get(url).then(response => {
                    this.coches = response.data;
                });
            }
        },
        mounted() {
            this.loadCoches();
        }
    }
</script>

<style>

</style>