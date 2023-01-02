<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo" id="conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>

      <Box v-if="listaEstaVazia">
        Você não está muito produtivo hoje :(
      </Box>

    </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from '@/components/BarraLateral.vue';
import Formulario from '@/components/Formulario.vue';
import Tarefa from '@/components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa';
import Box from '@/components/Box.vue'


export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box
  },
  data () {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false,
    }
  },
  computed:{
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0;
    }
  },
  methods:{
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo

    }
  }
});
</script>

<style>

  .lista{
    padding: 1.25rem;
  }

  @media (max-width: 500px){
    .lista{
      min-height: 500px;
    }
  }

 


  main{
    --bg-primario: #fff;
    --texto-primario: #000;
    --sombra: 0 0.5em 1em -0.125em rgb(10 10 10 / 10%), 0 0 0 1px rgb(10 10 10 / 2%);
  }

  main.modo-escuro{
    --bg-primario: #2b2d42;
    --texto-primario: #ddd;
    --sombra: 0 0.5em 1em -0.125em rgb(200 200 200 / 10%), 0 0 0 1px rgb(200 200 200 / 2%);
  }

  .conteudo{
    background-color: var(--bg-primario);
  }

  .box{
    box-shadow: var(--sombra);
  }
 

</style>
