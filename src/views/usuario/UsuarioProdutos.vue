<template>
    <section>
        <h2>adicionar Produto</h2>
        <ProdutoAdicionar/>
        <h2>Seus Produtos</h2>
        <transition-group v-if="usuario_produtos" name="list" tag="ul">
            <li v-for="(produto, index) in usuario_produtos" :key="index">
                <p>{{produto.descricao}}</p>
            </li>
        </transition-group>
        {{usuario_produtos}}
    </section>
   
</template>

<script>
import ProdutoAdicionar from "@/components/ProdutoAdicionar.vue";
import { mapState, mapActions } from "vuex";

export default {
    name: "UsuarioProdutos",
    components: {
        ProdutoAdicionar
    },
    computed: {
        ...mapState(["login", "usuario", "usuario_produtos"])
    },
    methods: {
        ...mapActions(["getUsuarioProdutos"])
    },
    watch: {
        login() {
            this.getUsuarioProdutos();
        }
    },
    created() {
        if(this.login) {
            this.getUsuarioProdutos();
        }    
    }
};
</script>

<style>

</style>