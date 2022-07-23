<template>
  <div class="content-todos__wrapper">
    <template v-if="props.todos.length > 0">
        <todos-item
            v-for="(todo, index) in props.todos"
            :key="index"
            :id="todo.id"
            :title="todo.title"
            @on-del="delHandler"
            @on-edit="editHandler"
        />
    </template>
    <div v-else>Todo is empty!</div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import TodosItem from './TodosItem.vue';

const emit = defineEmits(['onDel', 'onEdit']);
const props = defineProps({
    todos: {
        type: Array,
        default: [],
    }
});

const delHandler = (todoId) => {
    emit('onDel', todoId);
}

const editHandler = (todoId) => {
    emit('onEdit', todoId);
}
</script>
