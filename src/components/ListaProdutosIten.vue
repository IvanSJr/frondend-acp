<template>
<tbody>
    <tr>
        <td>{{produto.codigo}}</td>
        <td>{{produto.nome}}</td>
        <td>{{produto.preco}}</td>
        <td>{{produto.categoria}}</td>
        <td>
            {{produto.status}}
            <i class="fa fa-check align-center" :class="classeCSS"></i>
        </td>
        <td>
            <button class="btn"><i class="fa fa-edit"></i></button>
            <button class="btn"> <i class="fa fa-trash"></i></button>
        </td>
    </tr>
</tbody>
</template>

<script>
export default {
    props: {
        produto: {
            type: Object,
            require: true
        }
    },
    computed: {
        classeCSS() {
            return {
                'btn-success': this.produto.status == 'EM_ESTOQUE',
                'btn-warning': this.produto.status == 'BAIXO_ESTOQUE',
                'btn-danger': this.produto.status == 'SEM_ESTOQUE' 
            }
        }
    }
}
</script>
