<template>
  <div id="app">
 
    <addtodo v-on:add-todo="addtodo" />
    <ToDos v-bind:todos="todos"  v-on:del-todo="deleteTodo"/>
 
  </div>
</template>

<script>
 import ToDos from '../components/Todos.vue';
//  import headerTop from '../components/layouts/headerTop.vue';
 import addtodo from '../components/addtodo.vue';
 import axios from 'axios';
import { constants } from 'fs';
export default {
  name: 'Home',
  components: {
  //  headerTop,
    ToDos,
    addtodo

   
  },
  data()
  {
    return {
      todos:
      [
        
      ],
      msg:'Hellow'
    }
  },
  created()
  {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos=res.data)
    .catch(err=> console.log(err));

  },
  
  methods:{
    deleteTodo(id)
    {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then( this.todos=this.todos.filter(todo=>todo.id!=id))
      .catch(err=>console.log(err));
    //  this.todos=this.todos.filter(todo=>todo.id!=id);

    },
    addtodo(newTodoObj)
    {
      const {title,completed}=newTodoObj;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        completed
      })
      .then(res=>this.todos= this.todos=[...this.todos,newTodoObj])
      .catch(err=>console.log(err));
     // this.todos=[...this.todos,newTodoObj];

    }
  }
  
}
</script>

<style> 
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
