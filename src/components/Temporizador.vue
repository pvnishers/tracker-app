<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
      <CronometroForm :tempoEmSegundos="tempoEmSegundos"/>
      <BotaoForm @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
      <BotaoForm @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />
    </section>
  </template>
  

<script lang="ts">
import { defineComponent } from "vue";
import CronometroForm from "./Cronometro.vue";
import BotaoForm from "./Botao.vue";

export default defineComponent({
    name: "TemporizadorForm",
    emits: ['aoTemporizadorFinalizado'],
    components: {
        CronometroForm,
        BotaoForm
    },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false
        };
    },
    methods: {
        iniciar() {
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000);
            console.log("iniciando");
        },
        finalizar() {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        },
    },
});
</script>
