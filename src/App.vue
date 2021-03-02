<template>
  <div id="app">
    <div>
      <CreateTodo
          v-on:addTodo="addTodo"
      />
      <select v-model="filter" >
        <option value="all">Все</option>
        <option value="completed">Отмеченые</option>
        <option value="not-completed">Не отмеченые</option>
      </select>
    </div>
    <TodoList
      v-bind:todos="todosFilter"
      v-on:remove="remove"
    />
  </div>
</template>

<script>

import TodoList from "@/components/TodoList";
import CreateTodo from "@/components/CreateTodo";

export default {
  name: 'App',
  data () {
    return {
      todos : [],
      filter : 'all'
    }
  },

  components: {
    TodoList,CreateTodo
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(response => response.json())
    .then(data => {
      this.todos = data;
    })
  },
  methods: {
    remove(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  computed : {
    todosFilter (){
      if(this.filter === 'all') {
         return this.todos
      }

      if(this.filter === 'completed') {
        return this.todos.filter(todo => todo.completed)
      }

      if(this.filter === 'not-completed') {
        return this.todos.filter(todo => !todo.completed)
      }

    }
  }
}
</script>

<style scoped>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  select{
    border-radius: 5px;
    height: 40px;
    border: 1px solid #ccc;
    padding-left: 10px;
    cursor: pointer;
    margin: 20px auto 5px;
  }

</style>
