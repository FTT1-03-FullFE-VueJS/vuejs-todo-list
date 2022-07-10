<template>
  <div class="app-content__wrapper">
    <div class="app-content__top">
      <content-control />
      <content-form
        :is-show-form="isShowForm"
        :todo-input="todoInput"
        :todo-selected="todoSelected"
        @on-toggle="toggleForm"
        @on-input="inputChangeHandler"
        @on-store="storeHandler"
        @on-update="updateHandler"
      />
    </div>
    <div class="app-content__bottom">
      <content-todos
        :todos="todos"
        @on-del="delHandler"
        @on-edit="editHandler"
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
const todoSelected = ref(null);
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

const delHandler = (todoId) => {
    const todoIndex = todos.value.findIndex(todo => todo.id === todoId);
    if (todoIndex >= 0) {
        todos.value.splice(todoIndex, 1);
    } else {
        alert('This todo is not defined');
    }
}

const editHandler = (todoId) => {
    const todoIndex = todos.value.findIndex(todo => todo.id === todoId);
    if (todoIndex >= 0) {
        isShowForm.value = true;
        todoSelected.value = todos.value[todoIndex];
        todoInput.value = todoSelected.value.title;
    } else {
        alert('This todo is not defined');
    }
}

const updateHandler = () => {
    if (todoInput.value.trim().length) {
        const todoIndex = todos.value.findIndex(todo => todo.id === todoSelected.value.id);
        todos.value[todoIndex] = {
            ...todos.value[todoIndex],
            title: todoInput.value
        };
        todoInput.value = null;
        todoSelected.value = null;
        isShowForm.value = false;
    } else {
        alert('Please enter new todo to update!');
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
