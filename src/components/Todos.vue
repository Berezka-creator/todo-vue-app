<template>
  <div>
    <ul>
      <li v-bind:key="todo.id" v-for="todo of todos">
        <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"/>
      </li>
    </ul>
  </div>
</template>

<script>
import Todo from './Todo';

export default {
  name: 'Todos',
  components: {
    Todo

  },
  props: [
    "todos"
  ]
}
</script>
<style scoped>
li{
  list-style-type: none;

}
</style>
