<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <h3>You have {{ todosCount }} todos!</h3> -->
    <div>
      <input v-model="newTodoName" @keyup.enter="addTodo" type="text" placeholder="add a todo">
    </div>
    <div>
      <ul>
        <li v-for="todo in todos" :key="todo.id">
          <span>{{todo.name}}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>

</template>


<script>
import { ref } from 'vue'

export default {
  setup(){
    let newTodoName =  ref('')
    let todos = ref ([])
    const swearwords = ['fart', 'butt hair', 'willy']

    function addTodo(){
      let newTodo = {
        id: Date.now(),
        name: this.newTodoName.v
      }
      todos.value.push(newTodo)
      newTodoName.value = ''
    },
      deleteTodo(index){
      this.todos.splice(index,1)
    }
      }
    }

    return{
      newTodoName,
      todos
    }
  }
  // data(){
  //   return{
  //     newTodoName:'',
  //     todos:[
  //       
  //     ],
  //     swearwords: ['fart', 'butt hair', 'willy']
  //   }
  // },
  // computed:{
  //   todosCount() {
  //     return this.todos.length
  //   }
  // },
  // methods: {
  //   addTodo(){
  //     let newTodo = {
  //       id: Date.now(),
  //       name: this.newTodoName
  //     }
  //     this.todos.push(newTodo)
  //     this.newTodoName = ''
  //   },
  //   deleteTodo(index){
  //     this.todos.splice(index,1)
  //   }
  // },
  // watch: {
  //   newTodoName(newValue){
  //     console.log('newValue: ', newValue)
  //     if(this.swearwords.includes(newValue.toLowerCase())){
  //       this.newTodoName=''
  //       alert('You must NEVER say'+ newValue + '!!')
  //     }
  //   }
  // }
  }

</script>

<style>
ul{
  list-style: none;
  padding: 0;
  width: 200px;
  margin: 20px auto 0;
}
li {
  border: 1px solid;
  display: flex;
  margin-bottom: 10px;
}
li span{
  flex-grow: 1;
}
</style>
