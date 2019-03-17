<template>
    <div>
        <h1>ToDos</h1>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <ToDoItem v-bind:todo="todo"/>
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

