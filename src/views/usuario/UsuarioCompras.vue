<template>
    <div v-if="compras">
        <h2>Compras</h2>
        <div class="prdutos-wrapper" v-for="(compra, index) in compras"
        :key="index">
        <ProdutoItem v-if="compra.produto" :produto="compra.produto">
            <p class="vendedor">
                <span>Vendedor:</span>
                {{compra.vendedor_id}}
            </p>
        </ProdutoItem>
        </div>

    </div>
</template>

<script>
import ProdutoItem from "@/components/ProdutoItem.vue"
import {api} from "@/services.js"
import { mapState } from "vuex";

export default {
    components: {
        ProdutoItem,
    },
    data() {
        return {
            compras: null,
        }
    },
    computed: {
        ...mapState(["usuario", "login"])
    },
    methods: {
        getCompras() {
        api.get(`/transacao?comprador_id=${this.usuario.id}`).then(response => {
            this.compras = response.data;
        })
        }
    },
    watch: {
        login() {
            this.getCompras();
        }
    },
    created() {
        if (this.login) {
            this.getCompras();
        }
    } 
}
</script>

<style scoped>

.produto-wrapper {
    margin-bottom: 40px;
}

.vendedor span {
    color: #e80;
}

.entrega {
    display: grid;
    grid-template-columns: minmax(100px, 200px) 1fr;
    grid-gap: 20px;
    margin-bottom: 60px;
}

h2 {
    margin-bottom: 20px;
}

h3 {
    margin: 0px;
    justify-self: end;
}

</style>