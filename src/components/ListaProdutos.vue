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
      produtos : [],
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
