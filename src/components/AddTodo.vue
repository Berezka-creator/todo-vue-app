<template>
  <div>
    <form @submit="addTodo">
      <label for="TodoOptions">Type your Todo:</label>
      <input type="text" v-model="title" name="title" list="todosList" id="TodoOptions">
      <datalist id="todosList">
        <option v-for="item in items" v-bind:key="item.id"  class="single-blog">
          {{item.title}}
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

  created() {
    this.$http.get('https://jsonplaceholder.typicode.com/todos').then(function(data){
      console.log(data);
      this.items=data.body.slice(0,10);
      console.log("this.items")
      console.log(this.items)

    })


  }
}
</script>
<style scoped>
input{
  padding: 10px 10px;
  border-radius: 10px;
  border: 3px solid #00abeb;

  }
input:focus {
  background-color: lightblue;
}

</style>
