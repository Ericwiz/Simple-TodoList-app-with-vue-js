<template>
    <div class="d-flex">
        <v-text-field 
        variant="solo" class="rounded-lg mr-3" 
        :value="modelValue" 
        @input="$emit('update:modelValue', $event.target.value)"
        :rules="rules"
        />
        <v-btn color="success" class="mt-2" @click="$emit('addNewTodo')">Add</v-btn>
    </div>
</template>

<script>
    export default {
        props: ['modelValue'],
        emits: ['update:modelValue', 'addNewTodo'],
        
        data() {
            return {
                rules: [
                    value => {
                    if (value) return true

                    return 'Enter todo'
                    },
                ],
            }
        }
    }
</script>

<style scoped>
</style> 