<template>
  <div class="content-todos__wrapper">
    <todos-item
        v-for="(todo, index) in todos"
        :key="index"
        :id="todo.id"
        :title="todo.title"
    />
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import TodosItem from './TodosItem.vue';

const props = defineProps({
    todos: {
        type: Array,
        default: [],
    }
});
</script>
