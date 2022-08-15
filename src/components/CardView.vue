<template>
  <div class="container">
    <div class="d-flex justify-content-center">
       <form class="p-3 w-50" @submit.prevent="addTodo"> 
          <div class="form-group text-center">
            <img src="../assets/download.jpg" width="100">
          </div>
          <div class="form-group">
            <input type="text" placeholder="First Name" class="form-control" v-model="firstname">
          </div>
          <div class="form-group">
            <input type="text" placeholder="Last Name" class="form-control" v-model="lastname">
          </div>
          <div class="form-group">
            <button type="submit" class="btn btn-primary form-control">submit</button>
          </div>
       </form>
    </div>
    <span></span>
    <div v-for="todo of todos" :key="todo" class="card w-50 mt-2 p-2">
      <div class="d-flex justify-content-between">
        <div class="content">
          <p>First Name: {{todo.text1}} </p>
          <p>Last Name: {{todo.text2}} </p>
        </div>
        <div class="icons">
          <li @click="removeTodo(id)" class="fa fa-trash"></li>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { reactive, ref } from '@vue/reactivity'
export default {
  setup() {
    const todos = reactive([]);
    const firstname = ref('');
    const lastname = ref('');

    function addTodo() {
      todos.unshift({
        text1: firstname.value,
        text2: lastname.value,
      })
      firstname.value = "",
      lastname.value = ""
    }
    function removeTodo(id) {
      if(!confirm('Are you sure to remove')) {
        return;
      }
      todos.splice(id, 1)
    }
    return { todos, firstname, lastname, addTodo, removeTodo };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
form, .card {
  border-radius: 8px ;
  margin: auto;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px, rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
}
p {
  display: flex;
  justify-content: start;
  color: black;
}
.card, form {
  border-top: 3px solid blue;
}
form {
  margin-top: 5rem;
}
.icons {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 25px;
  color:  red;
  cursor: pointer;
}
</style>
