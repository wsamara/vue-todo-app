<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo"/>


      <AddTodo  class="InputNewTodo" v-on:add-todo="addTodo"/>



  </div>
</template>


<script>
import Vue from "vue";
import {uuid} from "vue-uuid";
Vue.use(uuid);

import Header from './components/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
export default {
  name: 'app',
  components: {
    Header,
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: [

      {
        "id": uuid.v4(),
        "title": "Go workout",
        "completed": false
      },
      {
        "id": uuid.v4(),
        "title": "Do laundry",
        "completed": false
      },
      {
        "id": uuid.v4(),
        "title": "Cook food",
        "completed": false
      },
      {
        "id": uuid.v4(),
        "title": "Clean up room",
        "completed": false
      },
      {
        "id": uuid.v4(),
        "title": "Finish work",
        "completed": false
      }

      ]
    };
  },


  methods:{
    addTodo(newTodoObj){
      this.todos=[...this.todos, newTodoObj];
    },
    deleteTodo(todoId){
      this.todos = this.todos.filter(todo => todo.id !== todoId);

    }
  }
}
</script>
<style>
*{
  box-sizing: border-box;
  padding: 0;
  margin: 0;

}
#app{
  width: 680px;
  margin:0 auto;

}
</style>
