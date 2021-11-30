<template>
    <div>
        <h1>Pedidos</h1> 
<!--
    <button @click="getPedidos">Consultar</button>
-->
        <table class="table">
  <thead>
    <tr>
      <th scope="col">Id</th>
      <th scope="col">Cedula</th>
      <th scope="col">Nombre</th>
      <th scope="col">Telefono</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="pedido in pedidos" :key="pedido.id">
      <td>{{pedido.id}}</td>
      <td>{{pedido.cedula}}</td>
      <td>{{pedido.nombre}}</td>
      <td>{{pedido.telefono}}</td>
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
            pedidos : []
        }
    },
    methods : {
        async getPedidos() {
            const resp = await axios.get('http://127.0.0.1:8080/api/v1/pedidos')
            this.pedidos =resp.data
        }
    },
    mounted () {
       this.getPedidos() 
    }    
}
</script>