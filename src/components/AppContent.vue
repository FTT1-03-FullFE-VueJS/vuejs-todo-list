<template>
  <div class="app-content__wrapper">
    <div class="app-content__top">
      <content-control />
      <content-form
        :is-show-form="isShowForm"
        :todo-input="todoInput"
        @on-toggle="toggleForm"
        @on-input="inputChangeHandler"
        @on-store="storeHandler"
      />
    </div>
    <div class="app-content__bottom">
      <content-todos
        :todos="todos"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from '@vue/reactivity';
import ContentControl from './ContentControl.vue';
import ContentForm from './ContentForm.vue';
import ContentTodos from './ContentTodos.vue';
import { v4 as uuidv4 } from 'uuid';

// State of this component
const isShowForm = ref(false);
const todoInput = ref('');
const todos = ref([
    {
        id: uuidv4(),
        title: 'Đi chợ',
    },
    {
        id: uuidv4(),
        title: 'Học bài',
    },
    {
        id: uuidv4(),
        title: 'Học lập trình',
    },
]);

const toggleForm = () => {
    isShowForm.value = !isShowForm.value;
}

const inputChangeHandler = (value) => {
    todoInput.value = value;
}

const storeHandler = () => {
    if (todoInput.value.trim().length) {
        const newTodo = {
            id: uuidv4(),
            title: todoInput.value
        };
        todos.value.push(newTodo);
        todoInput.value = '';
        isShowForm.value = false;
    } else {
        alert('Please enter new todo to store!');
    }
}
</script>

<style>
.app-content__top {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
  align-items: center;
}
</style>
