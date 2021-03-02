<template>
  <li>
        <span v-bind:class="{com : todo.completed === true}">
          <input type="checkbox" v-if="todo.completed === false" v-on:change="todo.completed = !todo.completed">
          <input type="checkbox" v-else checked v-on:change="todo.completed = !todo.completed">
          {{index + 1}}
        </span>
    <p>{{todo.title}}</p>
    <button v-on:click="$emit('remove' , todo.id)"> &times; </button>
  </li>
</template>
<!--completed-->
<script>

  export default {
    props : {
      todo : {
          type: Object
      },
      index : {
        type: Number
      }
    },
  }

</script>

<style scoped>
  li {
    width: 80%;
    margin: 0 auto;
    padding: 5px 20px;
    box-shadow: 0 0 10px #ccc;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
  input{
    font-size: 20px;
    color: #666;
    margin-right: 10px;
    cursor: pointer;
  }
  p{
    font-size: 22px;
    color: #333;
  }

  button{
    width: 30px;
    height: 30px;
    font-size: 25px;
    color: #333;
    background: transparent;
    border: 0;
    box-shadow: 0 0 5px #ccc;
    border-radius: 3px;
    cursor: pointer;
    transition: .2s linear;
  }

  button:hover{
    background: #777;
    color: #fff;
  }

  .com{
    text-decoration: line-through;
  }



</style>