<template>
<div class="mb-3">
    <label>To add your to-do list, click <b-button pill variant="primary" type="button" v-on:click="openForm"> + </b-button></label>
    <div><br>
    </div>
    <form class="detail-box" v-show="isOpen">
        <div class="form-group">
            <label>To-do</label>
            <input class="form-control" type="text" v-model="title" />
        </div>
        <div class="form-group">
            <label>Description</label>
            <input class="form-control" type="text" v-model="description" />
        </div>
        <div>
            <b-button pill variant="primary" type="button" v-on:click="sendForm">Add to do</b-button>
            <b-button pill variant="danger" type="button" v-on:click="closeForm">Cancel</b-button>
        </div>
    </form>
</div>
</template>

<script>
/* eslint-disable */
export default {
    name: 'CreateTodo',
    data() {
        return {
            title: '',
            description: '',
            isOpen: false

        };
    },
    methods: {
        openForm() {
            this.isOpen = true
        },
        closeForm() {
            this.isOpen = false
        },
        sendForm() {
            if (this.title !== '' && this.description !== '') {
                const title = this.title;
                const description = this.description;
                //now emit an event
                this.$emit("create-todo", {
                    title: title,
                    description: description,
                    done: false
                });
                this.title = '';
                this.description = '';
                this.isOpen = false;
            }
        }
    }
};
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
    height: 250px;
    margin: 0 auto;
}
</style>
