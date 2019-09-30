<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <!--Bind event on-click for a function markComplete -->
        <input type="checkbox" name="markTodo" id="markTodo" v-on:click="markComplete" :checked="todo.completed"/>
        <strong>{{todo.title}}</strong>
        <i class="material-icons del" @click="$emit('del-todo',todo)" >delete</i>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props: ["todo"], // received props from another controller
        methods: { // create a method for this file
            markComplete() {
                /* eslint-disable */
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .todo-item{
        background-color: #f4f4f4;
        padding: 15px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete{
        text-decoration: line-through;
    }
    .del{
        float: right;
    }
    .del:hover{
        cursor: pointer;
        color: lightcoral;
    }
    .material-icons {vertical-align:-30%}
</style>