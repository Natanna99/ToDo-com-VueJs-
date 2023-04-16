<template>
  <TheHeader v-show="showHeader"/>
  <div>

    <h4 :class="ClassTitulo">Lista de tarefas:</h4>

    <div v-for="item in ToDos" :key="item.id" class="todo-item">
      <input type="checkbox" v-model="item.completed">
      {{ item.title }} - {{ item.completed }}
    </div>

    <h4 :class="ClassTitulo">Lista de tarefas não finalizadas:</h4>
    <div v-for="item in listaNaoExecutadas" :key="item.id" class="todo-item">
      {{ item.title }}
    </div>

    <h4 :class="ClassTitulo">Lista de tarefas finalizadas:</h4>
    <div v-for="item in listaExecutadas" :key="item.id" class="todo-item">
      {{ item.title }}
    </div>

  </div>

</template>

<script>
import TheHeader from './components/TheHeader.vue'

export default {
  name: 'App',
  components: {
    TheHeader
  },

  data(){
    return{
        ClassTitulo: "title",
        showHeader: false,
        ToDos: [
          {
            "userId": 1,
            "id": 1,
            "title": "Estudar Vue Js",
            "completed": false
          },
          {
            "userId": 1,
            "id": 2,
            "title": "Estudar CSS",
            "completed": false
          },
          {
            "userId": 1,
            "id": 3,
            "title": "Concluir HTML",
            "completed": false
          },
          {
            "userId": 1,
            "id": 4,
            "title": "Limpar mesa",
            "completed": true
          },
          {
            "userId": 1,
            "id": 5,
            "title": "Ler um manga",
            "completed": false
          },
          {
            "userId": 1,
            "id": 6,
            "title": "Assistir One Piece",
            "completed": false
          },
        ]
    }
  },

  computed: {
    listaNaoExecutadas(){
      return this.ToDos.filter(item => !item.completed);
    },

    listaExecutadas(){
      return this.ToDos.filter(item => item.completed);
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 60px;
}
.todo-item{
  color: rgb(83, 83, 83);
  margin: 0 0 5px 0;
  padding: auto;
}
.title{
  font-size: 20px;
  color: black;
}
</style>
