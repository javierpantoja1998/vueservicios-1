<template>
  <div>
    <h1>Empleados Oficio</h1>
    <table class="table table-dark">
        <thead>
            <th>APELLIDO</th>
            <th>OFICIO</th>
            <th>SALARIO</th>
        </thead>
        <tbody v-for="emp in empleadosOficio" :key="emp.idEmpleado" :value="emp.idEmpleado">
            <tr>
                <td>{{emp.apellido}}</td>
                <td>{{emp.oficio}}</td>
                <td>{{emp.salario}}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios';
import Global from './../Global';

export default {
    name: "EmpleadosOficio",
    methods: {
        loadEmpleados(){
            var request = "api/Empleados/EmpleadosOficio/"+this.$route.params.oficio;
            var url = Global.urlEmpleados + request;

            axios.get(url).then(response => {
                this.empleadosOficio = response.data;
            });
        },

    },
    watch: {
        '$route.params.oficio'(nextVal, oldVal) {
            if(nextVal != oldVal) {
                this.loadEmpleados();
            }
        }
    },
    mounted() {
        this.loadEmpleados();
    },
    data() {
        return {
            empleadosOficio: {}
        }
    }
}
</script>

<style scoped>
    table, tr, td, th {
        margin: 0 auto;
        border: 2px solid white;
    }
    th {
        border: 2px solid black;
        background-color: white;
        color: black;
    }
</style>