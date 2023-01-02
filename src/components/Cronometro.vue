<template>
    <section>
        <strong :class="{ 'display': displayOn, 'escuro': escuroOn }">
            {{ tempoDecorrido }}
        </strong>
    </section>
</template>


<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Cronometro',
    props: {    //propriedades que vem do pai
        tempoEmSegundos: {
            type: Number,
            default: 0
        },
        displayOn:{
            type: Boolean,
            default: true
        },
        escuroOn: {
            type: Boolean,
            default: false
        },
    },
    computed: {
      tempoDecorrido (): string {
        return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
      }
    },

})
</script>

<style scoped>
.display{
    color: var(--texto-primario);
}
.escuro{
    color: #333333;
}

</style>
