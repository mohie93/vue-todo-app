<template>
    <div>
        <form>
            <input type="text" name="title" class="form-control" placeholder="Add Todo...." v-model="title">
            <input type="button" value="Submit" class="btn btn-secondary" @click="addTodo">
        </form>
        <br>
    </div>
</template>

<script>
    export default {
        name: "AddTodoItem",
        data(){
            return {
                title: ""
            }
        },
        methods: {
            addTodo() {
                const newTodo = {
                    title:this.title,
                    completed:false
                };
                // send to parent
                this.$emit('add-todo', newTodo);
                this.title = "";
            }
        }
    }
</script>

<style scoped>
    form{
        padding: 15px;
    }
    input[type="text"]{
        float: left;
        width: 50%;
    }
    input[type="button"]{
        float: right;
    }
</style>