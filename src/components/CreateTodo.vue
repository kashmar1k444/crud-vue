<template>

  <div>
    <form v-on:submit.prevent="addTodo">
      <input v-model="title" type="text">
      <button>
        Добавить
      </button>
    </form>
  </div>

</template>


<script>

  export default {
    data () {
      return {
        title : '',
      }
    } ,
    methods : {
      addTodo(){
        if(this.title.trim()) {
            const newTodo = {
              id : Date.now(),
              title : this.title,
              completed : false
            }
            this.$emit('addTodo' , newTodo);
            this.title = '';
        }
      }
    }
  }

</script>


<style scoped>

  div{
    width: 60%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
  }

  input{
    width: 400px;
    height: 40px;
    border-radius: 5px;
    padding: 0 10px;
    border: 1px solid #ccc;
  }

  button{
    width: 90px;
    height: 40px;
    background: transparent;
    border-radius: 5px;
    border: 1px solid #ccc;
    margin: 0 20px;
    cursor: pointer;
  }


</style>