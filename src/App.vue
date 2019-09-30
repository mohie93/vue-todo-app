<template>
  <div id="app">
    <Header/>
    <AddTodoItem v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
  import Header from "./components/layout/Header";
  import Todos from "./components/Todos";
  import AddTodoItem from "./components/layout/AddTodoItem";
  import Axios from "axios"
  export default {
    name: 'app',
    components: {Todos, Header, AddTodoItem},
    data() {
      return {
        todosUrl: 'https://jsonplaceholder.typicode.com/todos',
        limit:'5',
        todos: [
        ]
      }
    },
    methods:{
      deleteTodo(todo){
        Axios.delete(`${this.todosUrl}/${todo.id}`)
                .then( () =>
                        this.todos = this.todos.filter(todoItem => {
                          return todoItem.id !== todo.id
                        })
                )
                // eslint-disable-next-line
                .catch(err => console.log(err))

      },
      addTodo(newTodo){
        const {title, completed} = newTodo;
        Axios.post(this.todosUrl, {title, completed})
                .then(res => this.todos= [...this.todos, res.data])
                // eslint-disable-next-line
                .catch(err => console.log(err))
      }
    },
    created() {
      Axios.get(`${this.todosUrl}?_limit=${this.limit}`)
        .then(res => this.todos =res.data)
        // eslint-disable-next-line
        .catch(err => console.log(err));
    }
  }
</script>

<style>
</style>
