<template>
  <FormularioVue @aoSalvarTarefa="salvarTarefa" />
  <div class="lista">
    <TarefaTracker v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
    <BoxVue v-if="listaEstaVazia"> Você não está muito produtivo hoje :( </BoxVue>
  </div>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue';
import FormularioVue from '../components/Formulario.vue';
import TarefaTracker from '../components/Tarefa.vue'
import BoxVue from '../components/Box.vue';
import ITarefa from '../interfaces/ITarefa';

export default defineComponent({
  name: 'TarefasVue',
  components: {
    FormularioVue,
    TarefaTracker,
    BoxVue
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
  }
})
</script>
  