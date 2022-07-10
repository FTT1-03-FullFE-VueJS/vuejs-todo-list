<template>
  <div class="todos-item">
    <div class="todos-item__title">{{ props.title }}</div>
    <div class="todos-item__controls">
      <div class="todos-item__controls-delete">
        <button
            type="button"
            @click="delHandler"
        >Delete</button>
      </div>
      <div class="todos-item__controls-edit">
        <button
            type="button"
            @click="editHandler"
        >Edit</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['onDel', 'onEdit']);
const props = defineProps({
    id: {
        type: String,
        required: true,
    },
    title: {
        type: String,
        required: true,
    }
});

const delHandler = () => {
    emit('onDel', props.id);
}

const editHandler = () => {
    emit('onEdit', props.id);
}
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
