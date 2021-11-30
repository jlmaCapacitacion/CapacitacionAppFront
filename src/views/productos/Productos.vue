<template>
    <div>
        <h1>Productos</h1> 
<!--
    <button @click="getProductos">Consultar</button>
-->
        <table class="table">
  <thead>
    <tr>
      <th scope="col">Id</th>
      <th scope="col">Descripcion</th>
      <th scope="col">Precio</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="producto in productos" :key="producto.id">
      <td>{{producto.id}}</td>
      <td>{{producto.descripcion}}</td>
      <td>{{producto.precio}}</td>
    </tr>   
  </tbody>
</table>       
        
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data () {
        return {
            productos : []
        }
    },
    methods : {
        async getProductos() {
            const resp = await axios.get('http://127.0.0.1:8080/api/v1/productos')
            this.productos =resp.data
        }
    },
    mounted () {
       this.getProductos() 
    }    
}
</script>