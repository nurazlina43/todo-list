<template>
<div>
    <h5>Completed Tasks: {{todos.filter(todo => todo.done == true).length}}</h5>
    <h5>Pending Tasks: {{todos.filter(todo => todo.done == false).length}}</h5>
    <Todo />
</div>
</template>

<script>
/* eslint-disable */
import Todo from './Todo'
export default {
    name: 'TodoList',
    components: {
        Todo
    },
    data() {
        return {
            todos: localStorage.hasOwnProperty("todos") ?
                JSON.parse(localStorage.getItem("todos")) :
                []
            // array has done prop which get true when todo is completed 
        }
    }

}
</script>

<style scoped>

</style>
