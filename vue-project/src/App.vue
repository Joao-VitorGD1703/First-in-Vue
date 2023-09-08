<script lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/formulario.vue';
import Tarefa from "./components/Tarefa.vue";
import type ITarefa from './interface/ITarefa';
import Box from "./components/Box.vue"
import  { defineComponent } from 'vue';

export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed:{
    listaEstaVazia () : boolean{
      return this.tarefas.length === 0
    }

  },
  methods:{
    salvarTarefa (tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    trcarOtema(modoEscuroAtivo : boolean){
      this.modoEscuroAtivo = modoEscuroAtivo

    }
  }
});
</script>

<template>
  <main class="columns is-gapless is-multiline mode-escuro" :class="{'modo-escuro' : modoEscuroAtivo}">
    <div class="column is-one-fifth">
      <BarraLateral @aoTemaAlterado="trcarOtema"/>
    </div>
    <div class="lista column is-four-fifths conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
      <Box v-if="listaEstaVazia">
        Você não esá muito produtivo hoje 
      </Box>
    </div>
  </main>
 
</template>

<style scoped>

.lista{
  padding: 1.25rem;
}
main{
  --bg-primario: #fff;
  --texto-primario: #252525;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;

}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
