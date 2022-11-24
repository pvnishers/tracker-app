<template>
    <BoxVue>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column">
                <CronometroForm :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxVue>
</template>

<script lang="ts">
import {defineComponent, PropType} from 'vue'
import CronometroForm from './Cronometro.vue';
import ITarefa from '@/interfaces/ITarefa';
import BoxVue from './Box.vue';

export default defineComponent({
    name: 'TarefaTracker',
    components: {
        CronometroForm,
        BoxVue
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
                required: true
        }
    }
})
</script>

