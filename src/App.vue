<template>
  <div id="app">
    <headerTop/>
    <addtodo/>
    <ToDos v-bind:todos="todos"  v-on:del-todo="deleteTodo"/>
 
  </div>
</template>

<script>
 import ToDos from './components/Todos.vue';
 import headerTop from './components/layouts/headerTop.vue';
 import addtodo from './components/addtodo.vue';

export default {
  name: 'app',
  components: {
    headerTop,
    ToDos,
    addtodo

   
  },
  data()
  {
    return {
      todos:
      [
        {
          id:1,
          title:"Todo One",
          completed:true
        },
         {
          id:2,
          title:"Todo Two",
          completed:true
        },
         {
          id:3,
          title:"Todo Three",
          completed:false
        }
      ],
      msg:'Hellow'
    }
  },
  methods:{
    deleteTodo(id)
    {
      this.todos=this.todos.filter(todo=>todo.id!=id);

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
