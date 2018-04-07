<template>
  <div id="app">
    <img src="./assets/logo.png">

    <div class="input-group">
      <input v-model="novaTarefa" @keyup.enter="cadastrarNovaTarefa"/>
      <button type="button" @click="cadastrarNovaTarefa">Adicionar</button>
      <input type="checkbox" v-model="mostrarLidos">Mostrar Lidos
    </div>
    <lista-tarefa :tarefas="tarefasFiltradas" @lido="lerTarefa"/>
  </div>
</template>

<script>
import ListaTarefa from './components/ListaTarefa';

export default {
  name: 'app',
  components: {
    ListaTarefa,
  },
  data () {
    return {
      novaTarefa: '',
      mostrarLidos: false,
      tarefas: [
        { text: 'tarefa exemplo', lido: false, },
      ],
    }
  },
  methods: {
    cadastrarNovaTarefa() {
      if (this.novaTarefa.trim()) {
        this.tarefas.unshift({ text: this.novaTarefa, lido: false });
        this.novaTarefa = '';
      } 
    },
    lerTarefa(evt) {
      this.tarefas[evt].lido = !this.tarefas[evt].lido;
    },
  },
  computed: {
    tarefasFiltradas() {
      if (this.mostrarLidos) {
        return this.tarefas;
      }
      return this.tarefas.filter(t => !t.lido);
    },
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.input-group {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40%;
  margin: 0 auto;
}

.input-group input {
  min-width: 300px;
  height: 30px;
}

.input-group button {
  height: 36px;
  background-color: #42b983;
  border: none;
  color: white;
  font-size: 1rem;
  padding: 0 10px;
}

h1, h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}
</style>
