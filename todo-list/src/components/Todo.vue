<template>
<div>
    <form class="detail-box mb-3" v-show="!isEditing">
        <div class="d-flex" style="justify-content: space-between">
            <div class="text">
                <h4>To-do: {{todo.title}}</h4>
                <h6>Description: {{todo.description}}</h6>
            </div>
            <div class="pt-12 pr-2">
                <i v-b-tooltip.hover title="Edit" v-on:click="editTodo" class="fas fa-edit"></i>
                <i v-b-tooltip.hover title="Delete" v-on:click="deleteTodo(todo)" class="fas fa-trash-alt"></i>
            </div>
        </div>
        <div>
            <b-button pill variant="warning" type="button" v-on:click="completeTodo(todo)" v-show="!todo.done">Pending</b-button>
            <b-button pill variant="success" type="button" v-show="todo.done">Completed</b-button>
        </div>
    </form>
    <div class="mb-4" v-show="isEditing">
        <form class="detail-box ht-250">
            <div class="form-group">
                <label>Title</label>
                <input class="form-control" type="text" v-model="todo.title" />
            </div>
            <div class="form-group">
                <label>Description</label>
                <input class="form-control" type="text" v-model="todo.description" />
            </div>
            <div>
                <b-button pill type="button" v-on:click="closeForm">Close</b-button>
            </div>

        </form>
    </div>
</div>
</template>

<script>
/* eslint-disable */
export default {
    app: "Todo",
    props: ["todo"],
    data() {
        return {
            isEditing: false
        }
    },
    methods: {
        completeTodo(todo) {
            this.$emit('complete-todo', todo);
        },
        deleteTodo(todo) {
            this.$emit('delete-todo', todo);
        },
        editTodo() {
            this.isEditing = true;
        },
        closeForm() {
            this.isEditing = false;
        }
    }

}
</script>

<style scoped>
input[type="text"] {
    margin: 0 auto;
    width: 80%;
}

.detail-box {
    padding: 5px;
    border: 1px solid lightgrey;
    width: 350px;
    min-height: 155px;
    margin: 0 auto;
}

.ht-250 {
    height: 250px;
}

.text {
    text-align: left;
    padding: 5px;
}

.pt-12 {
    padding-top: 12px;
}
</style>
