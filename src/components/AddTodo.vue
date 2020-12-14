<template>
  <div>
    <form @submit="addTodo">

      <input placeholder="Add your todo ..." type="text" v-model="title" name="title" id="TodoOptions">


    </form>
  </div>
</template>

<script>
import Vue from "vue";
import {uuid} from "vue-uuid";
Vue.use(uuid);
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
      items:[]
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodoObj = {
        "id": uuid.v4(),
        "title": this.title,
        "completed": false
      }
      this.$emit('add-todo', newTodoObj);
      console.log("newTodoObj");
      console.log(newTodoObj);
      this.title = '';
    }
  },


}
</script>
<style scoped>
input{
  margin-top: 30px;
  padding: 10px 10px;
  }
</style>
