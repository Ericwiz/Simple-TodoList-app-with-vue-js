<template>
    <div>
        <AddTodo v-model="tasks" @addNewTodo="addTodo"/>
    </div>
    <TheTodos :myTodo="activeStore" @completed="completedTodo"/>
</template>

<script>
let id = 0
import AddTodo from './AddTodo.vue';
import TheTodos from './TheTodos.vue';

    export default {
    components: { TheTodos, AddTodo },

    data() {
        const storedTodos = localStorage.getItem('todoItems');
        return {
            todos: storedTodos ? JSON.parse(storedTodos) :[
                {
            ],
            tasks: ''
        }
    },

    computed: {
        activeStore() {
            return this.todos.filter(todo => !todo.done);
        }
    },

    methods: {
        addTodo () {
         this.todos.push({id: id++, task: this.tasks, done: false})
         this.tasks = ''
         localStorage.setItem("todoItems", JSON.stringify(this.todos));
         JSON.parse(localStorage.getItem('todoItems'))
        }, 

        completedTodo(todo) {
            todo.done = !todo.done
            localStorage.setItem("todoItems", JSON.stringify(this.todos));
        }
    },
}
</script>

<style scoped>

</style>