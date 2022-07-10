<template>
  <div class="content-todos__wrapper">
    <todos-item
        v-for="(todo, index) in todos"
        :key="index"
        :id="todo.id"
        :title="todo.title"
        @on-del="delHandler"
        @on-edit="editHandler"
    />
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
