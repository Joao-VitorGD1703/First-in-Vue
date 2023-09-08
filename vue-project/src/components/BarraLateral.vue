<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: "BarraLateral",
    emits: ["aoTemaAlterado"],
    computed:{
        textBotao(){
            if(this.modoEscuroAtivo) return "Desativar modo escuro"
            else return "Ativar modo escuro"
        }
    },
    data(){
        return{
            modoEscuroAtivo: false
        }

    },
    methods:{
        alterarTema() {
            this.modoEscuroAtivo = !this.modoEscuroAtivo
            this.$emit("aoTemaAlterado", this.modoEscuroAtivo)

        }
    }
})

</script>

<template>
    <header>
        <h1>
            <img src="../assets/logo.png" alt="">
        </h1>
        <button class="button btn" @click="alterarTema">
            {{ textBotao }}
        </button>
    </header>
</template>

<style scoped>
*{
    padding: 0px;
    margin: 0px;
    box-sizing: border-box;
}
header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
}

img{
box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;

}

img:hover{
    box-shadow: rgba(0, 0, 0, 0.514) 0px 10px 25px;

}

.btn{
    padding: 5px 10px;
}

@media only screen and (max-width: 768px) {
    header {
        padding: 2.5rem;
        height: auto;
    }
}
</style>