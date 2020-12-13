<template>
  <div class="todoItem" v-bind:class="{ 'completed':todo.completed }">
    <p v-on:click="markComplete">{{ todo.title }}</p>
    <button @click="$emit('delete-todo', todo.id)">Delete</button>

  </div>
</template>
<script>
export default {
  name: 'Todo',
  props:[
      "todo"
  ],
  methods:{
    markComplete(){
      this.todo.completed = !this.todo.completed
    }
  }
}
</script>
<style scoped>
.completed{
  text-decoration: line-through;
}
.todoItem{
  display: flex;

  justify-content: space-between;
  padding: 15px 0;
  border-bottom: 1px solid #eaeaea;

}
p{
  color: darkblue;
  font-size: 20px;
}

button{

}

</style>
