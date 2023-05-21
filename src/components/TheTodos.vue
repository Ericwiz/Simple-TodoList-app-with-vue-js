<template>
    <div v-for="todo in myTodo" :key="todo.id" class="mb-2">
        <input v-model="todo.done" type="checkbox" @click="$emit('completed', todo)">
        <span :class="{'text-decoration-line-through': todo.done }" class="ml-3">{{ todo.task }}</span>
    </div>
</template>

<script>
    export default {
        components: {},
        props: {
        myTodo: Object
    },
    emits: ['completed'],

    data () {
        return {
            
        }
    },

}
</script>

<style scoped>

</style>