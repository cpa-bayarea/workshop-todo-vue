<template>
  <ul class="lista-tarefa"> 
    <li v-for="(tarefa, idx) in tarefas" :key="idx" @click="lerTarefa(idx)"
        :class="{ 'lido': tarefa.lido }"
    >
      {{ tarefa.text }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'listaTarefa',
  props: {
    tarefas: {
      type: Array,
      required: true,
    },
  },
  methods: {
    lerTarefa(index) {
      this.$emit('lido', index);
    },
  },
};
</script>

<style>
ul {
  list-style-type: none;
  padding: 0;
  width: 37%; 
  margin: 10px auto;

}

li {
  display: inline-block;
  margin: 0 10px;
  border: 1px solid #2c3e50; 
  padding: 12px;
  width: 100%;
}

.lido {
  color: red;
}
</style>
