<template>
    <div v-for="todo in completedStore" :key="todo.id" class="d-flex flex-space-between w-100">
        <div class="w-75">
            <input v-model="todo.done" type="checkbox" @click="completedTodo(todo)">
            <span :class="{'text-decoration-line-through': todo.done }" class="ml-3">{{ todo.task }}</span>
        </div>
        <v-btn @click="deleteTodo(todo)" flat class="d-inline align-self-end">
            <v-icon class="text-end" icon="mdi-delete" color="primary"></v-icon>
        </v-btn>
    </div>

    <v-btn @click="clearAll" color="red" class="float-right">Clear all</v-btn>
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
                { id: id++, task: "Cook rice", done: true},
                { id: id++, task: "Cook Yam", done: true},
                { id: id++, task: "Cook Beans", done: false },
            ],
            tasks: ''
        }
    },

    computed: {
        completedStore() {
            return this.todos.filter(todo => todo.done);
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
        },

        deleteTodo(todo) {
            this.todos = this.todos.filter(t => t != todo)
            localStorage.setItem("todoItems", JSON.stringify(this.todos));
        },

        clearAll() {
            this.todos = this.todos.filter(t => !t.done)
            localStorage.setItem("todoItems", JSON.stringify(this.todos));
        },
    },
}
</script>

<style scoped>

</style>