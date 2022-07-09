<template>
  <div class="todos-item">
    <div class="todos-item__title">{{ props.title }}</div>
    <div class="todos-item__controls">
      <div class="todos-item__controls-delete">
        <button>Delete</button>
      </div>
      <div class="todos-item__controls-edit">
        <button>Edit</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    id: {
        type: Number,
        required: true,
    },
    title: {
        type: String,
        required: true,
    }
});
</script>

<style>
.todos-item {
  display: flex;
  justify-content: space-between;
  background-color: rgb(237, 236, 236);
  box-sizing: border-box;
  padding: 5px;
  border-radius: 3px;
  margin-bottom: 3px;
}
.todos-item__controls {
  display: flex;
}
</style>
