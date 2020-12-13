<template>
  <div>
    <div id="show-blog"></div>
    <form  @submit="addTodo">
      <label for="TodoOptions">Type your Todo:</label>
      <input type="text" v-model="title" name="title" list="todosList" id="TodoOptions">
      <datalist id="todosList">
        <option v-for="todo in todos" v-bind:key="todo.id"  class="single-blog">
          {{todo.title}}
        </option>

      </datalist>


    </form>

  </div>
</template>

<script>

import Vue from "vue";
import {uuid} from "vue-uuid";
Vue.use(uuid);

export default {
  name: 'Request',

  data() {
    return {
      todos: [],
      title:''
    };
  },
  methods:{
    addTodo(e) {
      e.preventDefault();
      const newTodoObj = {
        uuid: uuid.v4(),
        title: this.title,
        completed: false
      }
      this.$emit('add-todo', newTodoObj);
      console.log(newTodoObj);
      this.title = '';
    }

  },

  created() {
    this.$http.get('https://jsonplaceholder.typicode.com/todos').then(function(data){
      console.log(data);
      this.todos=data.body.slice(0,10);

    })


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
  width: 480px;
  margin:0 auto;
  border: 1px solid red;
}
.InputNewTodo{
  display: none;
}
.forPlus{
  text-align: center;
}
.plus{
  height: 50px;
  width: 50px;
  font-size: 40px;
  color: white;
  background-color: lightblue;
  border: 1px solid lightblue;
  border-radius: 30px;
  cursor: pointer;
  margin: 10px 0;

}
.plus:hover{
  background-color: #00abeb;

}
</style>
