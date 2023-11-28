<template>
  <h1>{{ titulo }}</h1>
  <h1>{{ subtitulo }}</h1>

  <input :disabled="tarefas.length == 0" v-model="subtitulo" type="text" placeholder="Descrição">

  <div v-if="tarefas.length <= 0">
    Não há tarefas.
  </div>

  <div v-if="tarefas.length > 0">
    Existem {{ tarefas.length }} tarefas pendentes.
    <ul>
      <li v-for="(tarefa, id) in tarefas" :key="id"> {{ tarefa }} </li>
    </ul>
  </div>

  <button @click="tarefas = []">Limpar</button>

</template>

<script>

export default {
  name: 'lv-tarefas',
  data  () {
    return {
      titulo: 'Listagens de tarefas',
      subtitulo: 'Defina uma descrição',
      tarefas: []
    }
  },

  mounted() {
    setTimeout( () => {
      this.titulo = "novo título"
      this.tarefas = ['tarefa 1', 'tarefa 2', 'tarefa 3', 'tarefa 4']
    }, 3000)
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
