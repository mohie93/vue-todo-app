<template>
    <div>
        <!--Create a to-do with key id using v-for loop -->
        <div v-bind:key="todo.id" v-for="todo in todos">
            <!--assign to-do value to a bind object then send it as a property for TodoItem component -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo)"/>
        </div>
    </div>
</template>

<script>
    import TodoItem from "./TodoItem"; // import from outside
    export default {
        name: "Todos", // name of the component
        components:{
            TodoItem
        }, // components we call in this file
        props: ["todos"] // props we receive in this file
    }
</script>

<style scoped>
</style>