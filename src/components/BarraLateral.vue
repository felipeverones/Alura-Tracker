<template>
    <header>
        <h1>
            <img src="@/assets/logo.png" alt="">
        </h1>
        <button class="button" @click="alterarTema" :style="estilos">
          <i :class="textoBotao "></i>
        </button>
    </header>
</template>

<script lang="ts">

    import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'BarraLateral',
        emits: ['aoTemaAlterado'],
        data (){
          return{
            modoEscuroAtivo: false,
            estilos:{
              "width": '50px'
            }
          }
        },
        computed:{
          textoBotao (){
            if(this.modoEscuroAtivo){
              return 'fas fa-sun'
            }else{
              return 'fas fa-moon'
            }
          }
        },
        methods:{
          alterarTema(){
            this.modoEscuroAtivo = !this.modoEscuroAtivo /* muda pra true */
            this.$emit('aoTemaAlterado',this.modoEscuroAtivo) /* emite o evento */
          }
        }
    });
</script>


<style scoped>
header {
  text-align: center;

  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  } 
}
</style>