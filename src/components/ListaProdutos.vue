<template>
<div class="container">

    <h1 class="font-weight-ligh alig text-center">Crud usando VueJs e SpringBoot</h1>

    <table class="table table-striped table-bordered mt-4">
      <title>AAAA</title>
        <thead>
        <tr>
            <th>Codigo</th>
            <th>Nome</th>
            <th>Preço</th>
            <th>Categoria</th>
            <th>Status</th>
            <th>Manutenção</th>  
        </tr>
        </thead>
        <ListaProdutosIten
        v-for="produto in produtos"
          :key="produto.id"
          :produto="produto"
        />
    </table>
</div>
</template>

<script>
// import ProdutoServicos from '../services/ProdutoServicos'
import config from './../config/config'
import ListaProdutosIten from './ListaProdutosIten.vue'
import axios from 'axios'
export default {
  name: 'MyCrud',
  components: {
    ListaProdutosIten
  },
  data() {
    return {
      produtos : [
      {"id":1,"nome":"Produto1","preco":2.20,"codigo":"asdaa","categoria":"CATEGORIA_1","status":"EM_ESTOQUE"},
      {"id":2,"nome":"Produto2","preco":10.21,"codigo":"asdasasa","categoria":"CATEGORIA_3","status":"SEM_ESTOQUE"},
      {"id":3,"nome":"Produto3","preco":23.23,"codigo":"bssswwas","categoria":"CATEGORIA_2","status":"EM_ESTOQUE"},
      {"id":4,"nome":"Produto4","preco":30.23,"codigo":"csdassa","categoria":"CATEGORIA_1","status":"BAIXO_ESTOQUE"},
      {"id":5,"nome":"Produto5","preco":555.50,"codigo":"dsdasasa","categoria":"CATEGORIA_2","status":"BAIXO_ESTOQUE"},
      {"id":6,"nome":"Produto6","preco":501.0,"codigo":"esdaasa","categoria":"CATEGORIA_1","status":"SEM_ESTOQUE"},
      {"id":7,"nome":"Produto7","preco":502.21,"codigo":"fassasa","categoria":"CATEGORIA_3","status":"BAIXO_ESTOQUE"},]
    }
  },
  created() {
    axios.get(`${config.apiURL}/produto`)
      .then((response) => {
        console.log(response)
        this.produtos = response
      })
  }
  
}
</script>
