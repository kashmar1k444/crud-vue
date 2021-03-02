<template>
    <ul>
     <TodoItem
        v-for="(todo , i) in todos"
        v-bind:todo="todo"
        v-bind:index="i"
        v-on:remove="remove"
     />
    </ul>
</template>

<script>

import TodoItem from '@/components/TodoItem';

export default {
  props: ['todos'],
  components : {
    TodoItem
  },
  methods: {
    remove(id) {
      this.$emit('remove' , id);
    }
  }
}

</script>