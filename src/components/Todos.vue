<template>
    <div>
        <h1>ToDos</h1>
        <div v-bind:key="todo.id" v-for="todo in todos">

            <ToDoItem v-bind:todo="todo"  v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
    </div>
</template>
<script>
import ToDoItem from './TodoItem.vue';
export default {
    name:"ToDos",
    props:["todos"],
    components:{
        ToDoItem
    },
    
}
</script>
<style scoped>

</style>

