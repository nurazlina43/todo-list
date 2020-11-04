<template>
<div>
    <form class="detail-box mb-3">
        <div>
            <div class="text">
                <h4>Title: {{todo.title}}</h4>
                <h5>Description: {{todo.description}}</h5>
            </div>
            <div class="pt-12 pr-2">
                <i v-b-tooltip.hover title="Edit" v-on:click="editTodo" class="fas fa-edit"></i>
                <i v-b-tooltip.hover title="Edit" v-on:click="deleteTodo(todo)" class="fas fa-trash-alt"></i>
            </div>
        </div>
        <div>
            <b-button pill variant="outline-success" type="button" v-on:click="completeTodo(todo)" v-show="!todo.done">Pending</b-button>
            <b-button pill variant="success" type="button" v-show="todo.done">Completed</b-button>
        </div>
    </form>
    <div>
        <form class="detail-box ht-250">
            <div class="form-group">
                <label>Title</label>
                <input class="form-control" type="text" />
            </div>
            <div class="form-group">
                <label>Description</label>
                <input class="form-control" type="text" />
            </div>
            <div>
                <b-button pill type="button">Close</b-button>
            </div>

        </form>
    </div>
</div>
</template>

<script>
/* eslint-disable */
export default {

}
</script>

<style scoped>

</style>
