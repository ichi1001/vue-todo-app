<template>
  <div id="app">
    <ul>
      <li v-for="todo in todos">
       <span>{{ todo.text }}</span>
       <span @click="deleteTodo(todo)">[x]</span>
      </li>
    </ul>
    <form @submit.prevent='addTodo'>
      <input type="text" v-model='newTodo'>
      <input type="submit" value="Add">
    </form>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
  return {
    todos: [
      { id: 1, text: 'dataを表示する' },
      { id: 2, text: 'ディレクティブを知る' }
    ],
    newTodo: ''
   }
  },
  methods: {
     addTodo: function() {
        const newId = Math.max.apply(null, this.todos.map(t => t.id)) + 1;
        this.todos.push({ id: newId, text: this.newTodo});
        this.newTodo = '';
     },
     deleteTodo: function(todo) {
        this.todos = this.todos.filter(item => item !== todo);
     },
  }
}

</script>

<style>

</style>
