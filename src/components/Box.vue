<template>
    <div class="box has-text-weight-bold" :style="estilos">
        <slot>

        </slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Box',
    data (){
        return {
            estilos: {
                'background': '#FAF0CA' /* backgroundColor tbm funciona */
            }
        }
    }
})
</script>

<style scoped>
    .box{
        /* background: #FAF0CA; */
        box-shadow: var(--sombra);
    }
</style>