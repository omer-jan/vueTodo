<template>
    <div class="todo-item" v-bind:class="{'is-complate':todo.completed}">
        <!-- v-bind:class="{{'is-complate':todo.completed}}" -->
          <input type="checkbox" v-on:change="markComplete">
        <p >{{todo.title}}</p>
    </div>
</template>
<script>
export default {
    name:"ToDoItem",
    props:["todo"],
    methods:
    {
        markComplete()
        {
            //console.log(123);

        }
    }
}
</script>
<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>

