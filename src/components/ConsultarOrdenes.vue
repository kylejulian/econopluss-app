<template>
    <div>
        <h2>Todos los registros</h2>
        <table>
            <tr>
                <th>Id</th>
                <th>Valor</th>
                <th>Gasto_Ingreso</th>
                <th>Clase de Registro</th>
                <th>Fecha</th>
                <th>Nota</th>
            </tr>
            <tr>
                <tr v-for="registro in registros" v-bind:key="registro.id_r">
                <td>{{registro.id_r}}</td>
                <td>{{registro.valor}}</td>
                <td>{{registro.tipo_registro}}</td>
                <td>{{registro.clase_registro}}</td>           
                <td>{{registro.fecha}}</td>
                <td>{{registro.nota}}</td>
            </tr>            
        </table>
    </div>
</template>

<script> 
import axios from "axios";
export default {
    
    name: "ConsultarOrdenes",
    data: function(){
        return {
            registros: [{
                id_r: 4,
                valor: 70000,
                tipo_registro: "gasto",
                clase_registro: "vivienda",
                fecha: "22-12-2020",
                nota: "Casi se nos cae la vaina",
            }]
        }
    },
    beforeCreate: function() {
        axios
      .get("http://127.0.0.1:8000/registros/consultar/")
      .then(respuesta => {
        this.registros = respuesta.data;
      })
      .catch(error => {
        console.log(error);
        alert("Error en la peticion con codigo" + error.response.status);
      });
    } 
}
</script>

<style scoped>

</style>