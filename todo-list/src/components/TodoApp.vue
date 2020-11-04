<template>
<div>
    <h1>TO-DO APP</h1>
    <TodoList :key="shouldUpdate" />
    <!-- add a listener to create-todo event  -->
    <CreateTodo v-on:create-todo="CreateTodo" />

</div>
</template>

<script>
/* eslint-disable */
import CreateTodo from './CreateTodo'
import TodoList from './TodoList'
export default {
    name: 'TodoApp',
    components: {
        CreateTodo,
        TodoList
    },
    data() {
        return {
            shouldUpdate: false
        }
    },
    methods: {
        CreateTodo(newTodo) {
            //save todo to local storage
            let todoArr = localStorage.hasOwnProperty("todos") ?
                JSON.parse(localStorage.getItem("todos")) : [];
            todoArr.push(newTodo);
            this.shouldUpdate = this.shouldUpdate;
            localStorage.setItem("todos", JSON.stringify(todoArr));

        }
    }
}
</script>
