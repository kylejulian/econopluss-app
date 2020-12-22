<template>
    <div id="CrearRegistro">
    <h3>Agregar Registro</h3>
    <label for="id_r" >Id</label>
    <input v-model="id_r" id="id_r" />
    <label for="valor">Valor</label>
    <input v-model="valor" id="valor" type="numeric"/>
    <label for="tipo_registro">tipo_registro</label>
    <input v-model="tipo_registro" id="tipo_registro"/>
    <label for="clase_registro">clase_registro</label>
    <input v-model="clase_registro" id="clase_registro"/>
    <label for="fecha">fecha</label>
    <input v-model="fecha" id="fecha" type="date"/>
    <label for="nota">nota</label>
    <input v-model="nota" id="nota"/> 
    <nav>
        <button v-on:click="crearRegistro">Agregar</button> 
    </nav>       
    </div>
</template>

<script>
import axios from"axios";
export default{
    name: "CrearRegistro",
    data: function(){
        return {
                id_r: "",
                valor: "",
                tipo_registro: "",
                clase_registro: "",
                fecha: "",
                nota: "",            
        };
    },

   methods: {

    crearRegistro: function() {
      var datosJSON = {
        id_r: this.id_r,
        valor: this.valor,
        tipo_registro: this.tipo_registro,
        clase_registro: this.clase_registro,
        fecha: this.fecha,
        nota: this.nota
      };
      axios
        .post("http://127.0.0.1:8000/registros/crear/", datosJSON)
        .then(respuesta => {
          alert(respuesta.data.mensaje);
        })
        .catch(error => {
          alert("error en el servidor");
        });
    }
  },
   

}

</script>

<style scoped>


</style>
