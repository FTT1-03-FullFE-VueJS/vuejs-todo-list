<template>
  <div class="app-content__wrapper">
    <div class="app-content__top">
      <content-control
        :search-input="searchInput"
        @on-search="changeSearchInput"
      />
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
        :todos="todosFiltered"
        @on-del="delHandler"
        @on-edit="editHandler"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, watch, computed } from 'vue';
import ContentControl from './ContentControl.vue';
import ContentForm from './ContentForm.vue';
import ContentTodos from './ContentTodos.vue';
import { v4 as uuidv4 } from 'uuid';

// State of this component
const isShowForm = ref(false);
const todoInput = ref('');
const searchInput = ref('');
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

const todosFiltered = computed(() => {
    const todosCoped = [...todos.value];
    const todosSearched = todosCoped.filter(todo => {
        const title  = todo.title.toLowerCase();
        const search = searchInput.value.toLowerCase();
        return title.includes(search);
    });

    return todosSearched;
});
/**
 * todos  = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]
 * search 'Thach' in "todos  = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]"
 * todosSearched = []
 * todos = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]
 *
 * search 'nhan' in "todos = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]"
 * return { title: 'nhan' }
 *
 * search 'Hung' in "todos = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]"
 * return { title: 'Hung' }
 */

// const searchHandler = () => {
//     const todosCoped = [...todos.value];
//     const todosSearched = todosCoped.filter(todo => {
//         const title  = todo.title.toLowerCase();
//         const search = searchInput.value.toLowerCase();
//         return title.includes(search);
//     });
//     todos.value = todosSearched;
// }
/**
 * todos  = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]
 * search = 'Thach' find "todos = [ { title: 'nhan' }, { title: 'Hung' }, { title: 'Phong' } ]"
 * => todosSearched = []
 * todos.value = todosSearched;
 * => todos.value = []
 * search = 'nhan' find "todos = []"
 */

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

const changeSearchInput = (value) => {
    searchInput.value = value;
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
